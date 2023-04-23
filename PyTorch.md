## Tensors
Torch tensors are Numpy arrays on steroids. These tensors are capable of automatic differentiation (using #autograd), and GPU acceleration.

## Data Primitives in PyTorch
`torch.utils.data.Dataset` - Stores data samples along with their labels `torch.utils.data.DataLoader` - Wraps an iterable around `Dataset` to easily access the samples

## Automatic Differentiation
`torch.autograd` module is responsible for tracking the operations performed on a tensor and calling the corresponding sequence of `tensor.grad_fn` when `tensor.backward()` is invoked.
Example:
```python
import torch

x = torch.ones(5) # input tensor
y = torch.zeros(3) # expected output

w = torch.randn(5, 3, requires_grad=True)
b = torch.randn(3, requires_grad=True)

z = torch.matmul(x, w)+b

loss = torch.nn.functional.binary_cross_entropy_with_logits(z, y)

loss.backward()

print(w.grad)
print(b.grad)
```

> [!note]
> - We can only obtain the `grad` properties for the leaf nodes of the computational graph, which have `requires_grad` property set to `True`. For all other nodes in our graph, gradients will not be available. In addition, we can only perform gradient calculations using `backward` once on a given graph, for performance reasons. If we need to do several `backward` calls on the same graph, we need to pass `retain_graph=True` to the `backward` call.
> - If we call `backward` for the second time with `retain_graph=True` and not zeroing the grads, the value of the gradient is different. This happens because when doing `backward` propagation, PyTorch **accumulates the gradients**, i.e. the value of computed gradients is added to the `grad` property of all leaf nodes of computational graph. If you want to compute the proper gradients, you need to zero out the `grad` property before. In real-life training an [[Optimizers]] helps us to do this.

### Disabling Gradient Tracking

By default, all tensors with `requires_grad=True` are tracking their computational history and support gradient computation. However, there are some cases when we do not need to do that, for example, when we have trained the model and just want to apply it to some input data, i.e. we only want to do *forward* computations through the network. We can stop tracking computations by surrounding our computation code with `torch.no_grad()` block:
```python
import torch 
x = torch.ones(5) # input tensor 
y = torch.zeros(3) # expected output 
w = torch.randn(5, 3, requires_grad=True) 
b = torch.randn(3, requires_grad=True)

z = torch.matmul(x, w)+b
print(z.requires_grad)

with torch.no_grad():
	z = torch.matmul(x, w)+b
print(z.requires_grad)
```

Another way to achieve the same result is to use the ``detach()`` method on the tensor:

```python
z = torch.matmul(x, w)+b
z_det = z.detach()
print(z_det.requires_grad)
```

> [!info] There are reasons you might want to disable gradient tracking:
> - To mark some parameters in your neural network at **frozen parameters**. This is a very common scenario for fine tuning a pre-trained network.
> - To **speed up computations** when you are only doing forward pass, because computations on tensors that do not track gradients would be more efficient.

Conceptually, #autograd keeps a record of data (tensors) and all executed operations (along with the resulting new tensors) in a **directed acyclic graph (DAG)** consisting of `torch.autograd.Function` objects. In this DAG, leaves are the input tensors, roots are the output tensors. By tracing this graph from roots to leaves, you can automatically compute the gradients using the chain rule.
In a forward pass, autograd does two things simultaneously:
-   run the requested operation to compute a resulting tensor
-   maintain the operation’s _gradient function_ in the DAG.

The backward pass kicks off when `.backward()` is called on the DAG root. `autograd` then:
-   computes the gradients from each `.grad_fn`,
-   accumulates them in the respective tensor’s `.grad` attribute
-   using the chain rule, propagates all the way to the leaf tensors.

### DAGs are dynamic in PyTorch

An important thing to note is that the graph is recreated from scratch; after each `.backward()` call, autograd starts populating a new graph. This is exactly what *allows you to use control flow statements in your model*; you can change the shape, size and operations at every iteration if needed.

## Tensor Gradients and Jacobian products

In many cases, we have a scalar loss function, and we need to compute the gradient with respect to some parameters. However, there are cases when the output function is an arbitrary tensor. In this case, PyTorch allows you to compute so-called **Jacobian product**, and not the actual gradient.
![[Algebra#^ef3bda]]

Instead of computing the Jacobian matrix itself, PyTorch allows you to compute **Jacobian Product**, $v^T \cdot J$  for a given input vector $v = \begin{pmatrix} v_1 & v_2 & \dots & v_m \end{pmatrix}$. This is achieved by calling `backward` with $v$ as an argument. The size of $v$ should be the same as the size of the original tensor, with respect to which we want to compute the product.
```python
inp = torch.eye(5, requires_grad=True)
out = (inp+1).pow(2)
out.backward(torch.ones_like(inp), retain_graph=True)
```

## Training Loop
```python
def train(dataloader, model, loss_fn, optimizer):
	size = len(dataloader)
	for batch_num, (X,y) in enumerate(dataloader):
		# Compute prediction and loss
		pred = model(X)
		loss = loss_fn(pred, y)

		# Backpropagation
		optimizer.zero_grad()
		loss.backward()
		optimizer.step()

		if batch_num % 100 == 0:
			loss, current = loss.item(), batch_num * len(X)
			print(f"loss: {loss:>7f} [{current:>5d}/{size:>5d}]")
```

## Test Loop
```python
def test(dataloader, model, loss_fn):
	size = len(dataloader)
	test_loss, correct = 0, 0

	with torch.no_grad():
		for X,y in dataloader:
			# Compute prediction and loss 
			pred = model(X)
			test_loss += loss_fn(pred, y).item()
			correct += (pred.argmax(1)==y).type(torch.float).sum().item()
			

	test_loss /= size
	correct /= size
	print(f"Test Error: \n Accuracy: {(100*correct):>0.1f}%, Avg Loss: {test_loss:>8f}")
```

## Model training
```python
# Initialize loss and optimizer
loss_fn = nn.CrossEntropyLoss()
optimizer = torch.optim.SGD(model.parameters(), lr=learning_rate)

epochs = 10
for t in range(epochs):
	print(f"Epoch {t+1}\n-------------------------")
	train_loop(train_loader, model, loss_fn, optimizer)
	test_loop(test_loader, model, loss_fn)
print("Done!")

# Saving the model
torch.save(model.state_dict(), "data/model.pth")
print("Saved Pytorch Model State to model.pth")
```

## [Efficient PyTorch Training loops](https://wandb.ai/wandb_fc/tips/reports/How-To-Write-Efficient-Training-Loops-in-PyTorch--VmlldzoyMjg4OTk5 )
We can make our training loops more efficient by leveraging Pytorch's **Automatic Mixed Precision (AMP)** package - `torch.amp`
The idea behind Automatic Mixed Precision is to conveniently use mixed precisions for different operations. Some operations like linear layers and convolutions, are much faster in lower precision floating point datatype - `(lower_precision_fp): torch.float16(half)`. While other operations, like reductions, often require the dynamic range of `torch.float32` 
Automatic Mixed Precision Training with datatype of `torch.float16` uses `torch.autocast` and `torch.cuda.amp.GradScaler` 

### Autocast in PyTorch
Instances of [`autocast`](https://pytorch.org/docs/stable/amp.html#torch.autocast "torch.autocast") serve as context managers or decorators that allow regions of your script to run in mixed precision.

In these regions, ops run in an op-specific dtype chosen by autocast to improve performance while maintaining accuracy. 

When entering an autocast-enabled region, Tensors may be any type. You should not call `half()` or `bfloat16()` on your model(s) or inputs when using autocasting.

[`autocast`](https://pytorch.org/docs/stable/amp.html#torch.autocast "torch.autocast") should wrap only the forward pass(es) of your network, including the loss computation(s). Backward passes under autocast are not recommended. Backward ops run in the same type that autocast used for corresponding forward ops.

One of the most common reasons for the **Out Of Memory (OOM) error** encountered in training large deep learning models is the problem of memory utilization. By default, PyTorch uses float32 to represent model parameters. For any decently sized model, that amounts to a lot of memory. If you have a decent accelerator with, say, 16GB of RAM, you probably won't be able to train bigger models. You probably won't even be able to compute a single forward pass through a batch of data. One possible solution to this problem is to automatically cast your tensors to a smaller memory footprint. Say float16 or even integer values!

#### Train loop with Autocast
```python
def train(dataloader, model, loss_fn, optimizer):
	size = len(dataloader)
	for batch_num, (X,y) in enumerate(dataloader):
		# ✨ Autocasting ✨
		with torch.cuda.amp.autocast():
			# Forward pass
			pred = model(X)
			# Compute Loss
			loss = loss_fn(pred, y)

		# Backpropagation
		optimizer.zero_grad()
		loss.backward()
		optimizer.step()

		if batch_num % 100 == 0:
			loss, current = loss.item(), batch_num * len(X)
			print(f"loss: {loss:>7f} [{current:>5d}/{size:>5d}]")
```

### Gradient Scaling
If the forward pass for a particular op has `float16` inputs, the backward pass for that op will produce `float16` gradients. Gradient values with small magnitudes may not be representable in `float16`. These values will flush to zero (“underflow” - Not to be confused with vanishing gradients, these gradients might contribute to the learning process but are skipped because of computational limits), so the update for the corresponding parameters will be lost.

To prevent underflow, “gradient scaling” multiplies the network’s loss(es) by a scale factor and invokes a backward pass on the scaled loss(es). Gradients flowing backward through the network are then scaled by the same factor. In other words, gradient values have a larger magnitude, so they don’t flush to zero.

Each parameter’s gradient (`.grad` attribute) should be unscaled before the optimizer updates the parameters, so the scale factor does not interfere with the learning rate.

#### Train loop with Autocast and Gradient Scaling
```python
def train(dataloader, model, loss_fn, optimizer):
	size = len(dataloader)
	scaler = torch.cuda.amp.GradScaler()
	for batch_num, (X,y) in enumerate(dataloader):
		# ✨ Autocasting ✨
		with torch.cuda.amp.autocast():
			## Forward pass
			pred = model(X)
			## Compute Loss
			loss = loss_fn(pred, y)

		# Backpropagation
		optimizer.zero_grad()
		## ✨ Scaling Gradients ✨
		scaler.scale(loss).backward()
		## ✨ Unscaling Gradients ✨
		scaler.step(optimizer)
		## ✨ Updating the Scale factor ✨
		scaler.update()

		if batch_num % 100 == 0:
			loss, current = loss.item(), batch_num * len(X)
			print(f"loss: {loss:>7f} [{current:>5d}/{size:>5d}]")
```

> [!info]
> **scaler.step(optimizer, \*args, \*\*kwargs)** operation carries out the following two operations:
> 1. Internally invokes `unscale_(optimizer)` (unless `unscale_()` was explicitly called for `optimizer` earlier in the iteration). As part of the `unscale_()`, gradients are checked for inf/NaNs.
> 2. If no inf/NaN gradients are found, invokes `optimizer.step()` using the unscaled gradients. Otherwise, `optimizer.step()` is skipped to avoid corrupting the params.
> `*args` and `**kwargs` are forwarded to `optimizer.step()`
> 
> **scaler.update()** 
> 1. If any optimizer steps were skipped the scale is multiplied by `backoff_factor` to reduce it. If `growth_interval` unskipped iterations occurred consecutively, the scale is multiplied by `growth_factor` to increase it.
> 

### Gradient Accumulation
While training LLMs, larger batch sizes lead to better convergence possibilities. But more often than not, we cannot fit large batches into our machine. Hence, we prefer something called Gradient Accumulation.
In Gradient accumulation, instead of running backprop after every forward prop, we compute a few forward props, accumulate the gradients and then run backprop. 
1. We normalize the loss with regard to the number of gradient accumulation steps
2. Only update the optimizer every chunk, the number of chunks being a number of steps/accumulation steps. Or at the end of the data loader.

#### Train loop with Autocast, Gradient Scaling and Accumulation
```python
def train(dataloader, model, loss_fn, optimizer):
	size = len(dataloader)
	NUM_ACC_STEPS = 4
	scaler = torch.cuda.amp.GradScaler()
	for batch_num, (X,y) in enumerate(dataloader):
		# ✨ Autocasting ✨
		with torch.cuda.amp.autocast():
			## Forward pass
			pred = model(X)
			## Compute Loss
			loss = loss_fn(pred, y)
			# Normalize the gradients
			loss /= NUM_ACC_STEPS
			
		# Backpropagation
		## ✨ Scaling gradients ✨
		scaler.scale(loss).backward()

		# ✨ Gradient Accumulation ✨
		if (batch_num + 1) % NUM_ACC_STEPS == 0 or batch_num + 1 == size: 
			optimizer.zero_grad()
			## ✨ Unscaling Gradients ✨
			scaler.step(optimizer)
			## ✨ Updating the Scale factor ✨
			scaler.update()

		if batch_num % 100 == 0:
			loss, current = loss.item(), batch_num * len(X)
			print(f"loss: {loss:>7f} [{current:>5d}/{size:>5d}]")
```

### Clearing up the Cache
Another method is to avoid the CUDA Out Of Memory Error altogether by always remembering to clean up your cache using `gc` and `torch` whenever possible in order to free up space.

```python
import gc

def train(dataloader, model, loss_fn, optimizer):
	size = len(dataloader)
	NUM_ACC_STEPS = 4
	scaler = torch.cuda.amp.GradScaler()
	for batch_num, (X,y) in enumerate(dataloader):
		# ✨ Autocasting ✨
		with torch.cuda.amp.autocast():
			## Forward pass
			pred = model(X)
			## Compute Loss
			loss = loss_fn(pred, y)
			# Normalize the gradients
			loss /= NUM_ACC_STEPS
			
		# Backpropagation
		## ✨ Scaling gradients ✨
		scaler.scale(loss).backward()

		# ✨ Gradient Accumulation ✨
		if (batch_num + 1) % NUM_ACC_STEPS == 0 or batch_num + 1 == size: 
			optimizer.zero_grad()
			## ✨ Unscaling Gradients ✨
			scaler.step(optimizer)
			## ✨ Updating the Scale factor ✨
			scaler.update()
		
		# ✨ Garbage Collection ✨
		torch.cuda.empty_cache()
		_ = gc.collect()
		
		if batch_num % 100 == 0:
			loss, current = loss.item(), batch_num * len(X)
			print(f"loss: {loss:>7f} [{current:>5d}/{size:>5d}]")
```

### PyTorch 2.0 Compiled model


```python
# default: optimizes for large models, low compile-time
#          and no extra memory usage
compiled_model = torch.compile(model)

# reduce-overhead: optimizes to reduce the framework overhead
#                and uses some extra memory. Helps speed up small models
compiled_model = torch.compile(model, mode="reduce-overhead")

# max-autotune: optimizes to produce the fastest model,
#               but takes a very long time to compile
compiled_model = torch.compile(model, mode="max-autotune")
```