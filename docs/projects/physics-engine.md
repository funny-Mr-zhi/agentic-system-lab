# 3D Physics Engine

目标：从 2D rigid body 开始，逐步实现 3D 碰撞、约束求解、可视化调试和稳定性实验。

参考项目：

- Box2D: https://github.com/erincatto/box2d
- Bullet3: https://github.com/bulletphysics/bullet3
- JoltPhysics: https://github.com/jrouwe/JoltPhysics
- PositionBasedDynamics: https://github.com/InteractiveComputerGraphics/PositionBasedDynamics

## Milestones

### M1: 2D Rigid Body

实现：

- vector/matrix
- position/velocity
- force/impulse
- Euler/semi-implicit Euler
- circles and boxes

必须能解释：

- force 和 impulse 的区别
- semi-implicit Euler 为什么通常更稳
- mass/inertia 如何进入方程

### M2: Collision

实现：

- broad phase
- AABB
- narrow phase
- contact point
- contact normal
- penetration depth

Codex 任务：

```text
请设计能暴露碰撞检测 bug 的可视化场景。
重点覆盖高速穿透、边角接触、堆叠抖动、接触法线翻转。
```

### M3: Constraint Solver

实现：

- sequential impulse
- friction
- restitution
- warm starting
- sleeping

### M4: 3D Upgrade

实现：

- quaternion
- sphere/box/capsule
- GJK/EPA 或 SAT
- contact manifold
- debug renderer

### M5: Stability Lab

实验：

- timestep sweep
- mass ratio sweep
- stack height
- friction/restitution matrix
- deterministic replay

## Completion

完成时你应该能解释：物理引擎的难点不只是公式，而是离散时间、数值误差、碰撞近似、约束迭代和可视化调试。
