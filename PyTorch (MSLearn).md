## Tensors
Torch tensors are Numpy arrays on steroids. These tensors are capable of automatic differentiation (using AutoGrad), and GPU acceleration.

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
> We can only obtain the `grad` properties for the leaf nodes of the computational graph, which have `requires_grad` property set to `True`. For all other nodes in our graph, gradients will not be available. In addition, we can only perform gradient calculations using `backward` once on a given graph, for performance reasons. If we need to do several `backward` calls on the same graph, we need to pass `retain_graph=True` to the `backward` call.

### Disabling Gradient Tracking

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

