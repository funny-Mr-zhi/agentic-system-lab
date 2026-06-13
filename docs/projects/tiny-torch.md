# Toy PyTorch

目标：从 scalar autograd 开始，逐步实现 tensor、broadcast、module、optimizer、训练循环，最后理解 PyTorch 的核心抽象。

参考项目：

- micrograd: https://github.com/karpathy/micrograd
- tinygrad: https://github.com/tinygrad/tinygrad
- minitorch: https://github.com/minitorch/minitorch
- Needle: https://github.com/dlsyscourse/needle

## Milestones

### M1: Scalar Autograd

实现：

- `Value`
- `+ - * / pow tanh relu exp log`
- topological sort
- reverse-mode autodiff
- 一个小 MLP

必须能解释：

- 为什么反向传播需要拓扑序？
- 梯度累加发生在哪里？
- 同一个节点被多次使用时会怎样？

Codex 任务：

```text
请为我的 scalar autograd 写 property tests，特别关注共享子图、重复 backward、数值梯度对照。
```

### M2: Tensor

实现：

- shape/stride
- contiguous storage
- elementwise ops
- matmul
- broadcasting
- reduction

必须能解释：

- view 和 copy 的区别
- stride 如何表达 transpose
- broadcast 的反向传播为什么需要 reduce

### M3: Neural Network API

实现：

- `Parameter`
- `Module`
- `Linear`
- `Sequential`
- SGD/Adam
- cross entropy

实验：

- XOR
- MNIST subset
- tiny regression

### M4: Execution And Performance

实现：

- eager execution baseline
- simple graph trace
- op fusion prototype
- NumPy backend 对照

思考：

- PyTorch 为什么动态图很舒服？
- tinygrad 为什么强调 lazy？
- kernel launch overhead 在哪里出现？

## Completion

完成时你应该能画出：

```text
Tensor -> Op -> Graph -> Backward -> Optimizer -> Training Loop
```

并能用自己的话解释：PyTorch 不是“魔法自动求导”，而是 tensor storage、计算图、链式法则、调度和后端 kernel 的组合。
