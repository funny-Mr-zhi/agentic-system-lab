# Reference Projects

调研日期：2026-06-13。

下面不是“最佳项目榜单”，而是适合拿来当手搓路线参照物的项目集合。选择标准：

- 代码和文档可读
- 范围足够小，可以完整建立 cognitive map
- 能暴露真实系统里的核心问题
- 适合与自己的实现做逐层对照

## 1. Toy OS / Kernel

参考：

- xv6: https://github.com/mit-pdos/xv6-public
- rCore Tutorial: https://github.com/rcore-os/rCore-Tutorial-v3
- Philipp Oppermann's Writing an OS in Rust: https://github.com/phil-opp/blog_os
- SerenityOS: https://github.com/SerenityOS/serenity

怎么用：

- xv6 用来理解 Unix 风格 kernel 的最小全貌。
- rCore 和 blog_os 用来学习现代 Rust/RISC-V 或 Rust/x86_64 的教学路径。
- SerenityOS 不适合作为第一版目标，但非常适合观察“从 hobby OS 长成完整系统”的目录组织和长期工程习惯。

## 2. Browser Engine

参考：

- Robinson: https://github.com/mbrubeck/robinson
- Web Browser Engineering: https://github.com/browserengineering/book
- Servo: https://github.com/servo/servo
- Ladybird: https://github.com/LadybirdBrowser/ladybird

怎么用：

- Robinson 是最适合手搓第一版的最小 browser engine：HTML、CSS、layout、paint 都能看到。
- Browser Engineering 适合按章节推进，尤其适合你自己实现并写注释。
- Servo 和 Ladybird 用来在后期理解真实 browser 的复杂性，别一开始就扎进去。

## 3. Kubernetes Homelab

参考：

- Kubernetes The Hard Way: https://github.com/kelseyhightower/kubernetes-the-hard-way
- ansible-kubernetes-the-hard-way: https://github.com/kelseyhightower/ansible-kubernetes-the-hard-way
- Jeff Geerling pi-cluster: https://github.com/geerlingguy/pi-cluster
- Flux CD: https://github.com/fluxcd/flux2
- k3s-ansible: https://github.com/k3s-io/k3s-ansible

怎么用：

- The Hard Way 用来理解 control plane 的每个组件和证书流。
- k3s-ansible 用来搭自己的可维护 homelab。
- Flux CD 用来把 GitOps 引入日常运维。

## 4. 8-bit CPU

参考：

- Ben Eater 8-bit computer: https://eater.net/8bit
- Nand2Tetris projects: https://github.com/nand2tetris/projects
- Digital logic simulator Logisim Evolution: https://github.com/logisim-evolution/logisim-evolution

怎么用：

- Ben Eater 用来做真实硬件路径。
- Nand2Tetris 用来补充从 NAND 到 assembler、VM、compiler 的系统层次。
- Logisim Evolution 用来在买零件或排线前验证电路设计。

## 5. Toy PyTorch

参考：

- micrograd: https://github.com/karpathy/micrograd
- tinygrad: https://github.com/tinygrad/tinygrad
- minitorch: https://github.com/minitorch/minitorch
- Needle: https://github.com/dlsyscourse/needle

怎么用：

- micrograd 用来理解反向传播的最小核心。
- minitorch 和 Needle 用来构建从 scalar autograd 到 tensor ops、broadcast、GPU backend 的课程式路径。
- tinygrad 用来观察极简框架如何做 lazy execution、kernel lowering 和 accelerator 支持。

## 6. Toy Database

参考：

- sqlite clone tutorial: https://github.com/cstack/db_tutorial
- BusTub: https://github.com/cmu-db/bustub
- MiniOB: https://github.com/oceanbase/miniob
- BoltDB: https://github.com/boltdb/bolt
- RisingLight: https://github.com/risinglightdb/risinglight

怎么用：

- cstack 的 sqlite clone 很适合第一版：页、表、B+Tree、简单 SQL。
- BusTub 适合系统性学习 buffer pool、execution engine、concurrency control。
- BoltDB 适合研究嵌入式 KV、B+Tree 和 mmap 风格工程。

## 7. 3D Physics Engine

参考：

- Box2D: https://github.com/erincatto/box2d
- Bullet3: https://github.com/bulletphysics/bullet3
- JoltPhysics: https://github.com/jrouwe/JoltPhysics
- Position Based Dynamics: https://github.com/InteractiveComputerGraphics/PositionBasedDynamics

怎么用：

- 先做 2D rigid body，再进 3D。
- Box2D 用来学习 broad phase、narrow phase、constraint solver 的清晰分层。
- Bullet/Jolt 用来后期对照 3D 碰撞和性能工程。
- PositionBasedDynamics 适合学习 cloth、rope、soft body 的另一套思路。

## 8. Tiny Claude Code / Coding Agent

参考：

- Aider: https://github.com/Aider-AI/aider
- OpenHands: https://github.com/All-Hands-AI/OpenHands
- SWE-agent: https://github.com/SWE-agent/SWE-agent
- OpenAI Codex CLI: https://github.com/openai/codex
- smolagents: https://github.com/huggingface/smolagents

怎么用：

- Aider 用来理解 patch/edit loop 和 repo-aware prompting。
- SWE-agent 用来理解 benchmark-driven agent harness。
- OpenHands 用来观察 sandbox、browser、terminal、workspace 的产品级编排。
- Codex CLI 用来理解现代本地 coding agent 的交互边界。

## Reading Protocol

读参考项目时固定问五个问题：

1. 它的最小状态是什么？
2. 哪些模块只负责 policy，哪些模块负责 mechanism？
3. 错误如何传播？
4. 测试如何表达核心 invariants？
5. 如果我要重写 1/10 版本，先保留哪些东西？
