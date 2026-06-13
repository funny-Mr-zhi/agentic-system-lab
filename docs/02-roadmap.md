# Roadmap

这是一个 18 个月路线，不要求每天推进，但要求每个阶段都产出可运行系统和复盘文档。

## Phase 0: 仓库启动，一周

目标：

- 建立实践目录。
- 为每个项目写 `reading.md`、`design.md`、`debug-log.md`、`retrospective.md`。
- 选定第一轮语言和工具链。

建议默认：

- OS: Rust 或 C
- Browser: Rust、Go 或 TypeScript
- Homelab: Ansible + k3s + Flux
- CPU: breadboard + Logisim
- Toy PyTorch: Python first，后续 C++/CUDA
- Database: C、Rust 或 Go
- Physics: C++ 或 Rust，配一个可视化 demo
- Agent: Python 或 TypeScript

## Phase 1: 三个快速闭环，1-3 个月

先做：

1. toy PyTorch
2. toy database
3. tiny coding agent

原因：

- 不需要复杂硬件。
- 每个项目都能很快看到可运行反馈。
- 三者正好覆盖数学计算、持久化系统、工具编排。

产出：

- 能训练一个 MLP 的 autograd engine。
- 能插入、查询、持久化的 B+Tree KV/SQL toy DB。
- 能读 repo、规划、调用 shell、生成 patch 的 tiny agent。

## Phase 2: 可视化系统，4-8 个月

推进：

1. browser engine
2. 3D physics engine

原因：

- 都需要大量可视化 debug。
- 都会逼你处理“算法正确但体验不对”的问题。
- 都很适合 Codex 帮你生成 fixtures 和 screenshot regression tests。

产出：

- 能解析 HTML/CSS，layout，paint，并支持少量 JS/event loop 的 browser。
- 能模拟 rigid body、碰撞、摩擦、关节约束的 physics sandbox。

## Phase 3: 硬核底层，9-14 个月

推进：

1. toy OS
2. 8-bit CPU

原因：

- 这两项慢，但认知收益极高。
- OS 让你理解软件如何接管硬件。
- CPU 让你理解硬件如何承载软件。

产出：

- 能 boot、分页、进程调度、系统调用、简单文件系统的 kernel。
- 能运行 microcode/assembly 程序的 8-bit CPU，最好同时有 Logisim 和实物版本。

## Phase 4: 真实环境，15-18 个月

推进：

1. Kubernetes homelab
2. 将前面项目部署、观测、备份

原因：

- homelab 不是单个项目，而是后续所有实验的地基。
- GPU 节点和边缘节点会自然逼你理解调度、存储、网络、可观测性和故障恢复。

产出：

- GitOps 管理的 k3s/Kubernetes 集群。
- Prometheus/Grafana/Loki 可观测性。
- Longhorn/TopoLVM/Ceph 之一的存储方案。
- 对 GPU workload、个人服务、实验服务的部署模板。

## Weekly Loop

每周固定做四件事：

1. 写一个最小功能。
2. 写一个观察工具。
3. 读一个参考模块。
4. 做一次 Codex review。

Codex review prompt 模板：

```text
请用 code review 的方式审查这个模块。
优先找 invariants 被破坏、边界条件、并发/资源泄漏、测试缺口。
不要泛泛表扬，按严重程度列出问题，并给出最小修复建议。
```

## Milestone Naming

每个项目都用同样的 milestone 命名：

- `m0-map`: 阅读参考项目并画模块图
- `m1-loop`: 最小可运行闭环
- `m2-state`: 明确核心状态和 invariants
- `m3-tests`: 引入测试、fixtures、replay
- `m4-perf`: benchmark 和 profiling
- `m5-rewrite`: 带着理解重写关键模块
- `m6-retro`: 复盘并写下一轮路线
