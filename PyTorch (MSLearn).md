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



---
[Reference](https://wandb.ai/wandb_fc/tips/reports/How-To-Write-Efficient-Training-Loops-in-PyTorch--VmlldzoyMjg4OTk5 )
#todo Training loop
#todo Testing loop
#todo Pytorch Autocast 
#todo GradScaler
#todo Gradient Accumulation
#todo Garbage Collection to prevent CUDA out of memory
#todo Pytorch 2.0 features