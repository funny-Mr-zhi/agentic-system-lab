<!-- # Computer Systems From Scratch -->
# Agentic Systems Lab

这个仓库的目标不是复刻几个 GitHub 项目，而是建立一套长期的“从第一性原理手搓系统”的训练场：每个项目都小到能由一个人完整掌控，大到足以暴露真实系统里的核心矛盾。

你会在这里按部就班实现八类系统：

1. toy Linux kernel
2. toy browser engine
3. home Kubernetes lab
4. 8-bit breadboard CPU
5. toy PyTorch
6. toy database
7. 3D physics engine
8. tiny Claude Code / coding agent

每个项目都遵循同一个学习循环：

1. 先读参考项目，画出 cognitive map。
2. 自己定义最小可运行版本。
3. 手搓第一版，故意保持朴素。
4. 加测试、可视化、日志和 benchmark。
5. 与参考项目对照，重构第二版。
6. 记录失败实验和设计取舍。
7. 让 Codex 帮你做代码审计、逆向阅读、测试生成和大胆实验。

## How To Use

从这里开始：

- [docs/00-intent.md](docs/00-intent.md): 仓库初衷与学习原则
- [docs/01-reference-projects.md](docs/01-reference-projects.md): GitHub 参考项目调研
- [docs/02-roadmap.md](docs/02-roadmap.md): 18 个月总路线
- [docs/03-codex-workflow.md](docs/03-codex-workflow.md): 高阶 Codex 用法
- [docs/04-git-workflow.md](docs/04-git-workflow.md): Git 分支、提交、版本和忽略规则
- [docs/projects](docs/projects): 八个项目的分阶段指南

实践区：

- `practice/`: 你的手搓代码
- `notes/`: 阅读笔记、实验记录、复盘
- `experiments/`: 对照实验、失败分支、性能测试
- `assets/`: 架构图、波形图、截图、白板图

## Suggested Order

推荐顺序不是按“难度最低”排，而是按认知复利排：

1. [tiny-torch](docs/projects/tiny-torch.md): 最快获得从标量自动微分到 tensor engine 的闭环反馈。
2. [database](docs/projects/database.md): 练 B+Tree、持久化、并发、查询执行，系统感很强。
3. [coding-agent](docs/projects/coding-agent.md): 反过来理解 Codex/Claude Code 这类工具的 harness engineering。
4. [browser](docs/projects/browser.md): 学解析、布局、渲染、事件循环和隔离。
5. [physics-engine](docs/projects/physics-engine.md): 学数值稳定性、碰撞、约束求解和可视化调试。
6. [toy-os](docs/projects/toy-os.md): 学启动、内存、进程、文件系统和驱动。
7. [k8s-homelab](docs/projects/k8s-homelab.md): 把分布式系统落到真实硬件和运维。
8. [8bit-cpu](docs/projects/8bit-cpu.md): 最慢但最硬核，从门电路走到 ISA。

当然，如果你已经有硬件热情，8-bit CPU 可以随时并行推进。它不像软件项目那样适合“晚上糊一版”，但非常适合周末专注。

## Definition Of Done

每个项目的完成标准不是“功能很多”，而是你能回答这些问题：

- 它的最小核心抽象是什么？
- 关键数据结构在哪里被维护？
- 哪些 invariants 一旦破坏就会崩？
- 最难 debug 的 bug 是什么，为什么？
- 参考项目为什么选择了不同设计？
- 如果从头再写，第一处会改哪里？

当你能带着这些问题读生产级系统，仓库就发挥作用了。
