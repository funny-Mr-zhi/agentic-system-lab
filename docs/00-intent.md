# Intent

`init.md` 里的核心情绪很清楚：你不是想“会用工具”，而是想把底层系统变成自己的后花园。现代 coding agent 的意义，也不是替你跳过理解，而是把查资料、搭骨架、做实验、写测试、追 bug 的摩擦降下来，让你有余力真正咬住原理。

这个仓库因此有三个原则。

## Principle 1: 手搓优先，参考第二

参考项目用于校准范围、发现盲点、学习工程边界，不用于复制粘贴。每个项目都要先写自己的最小版本，再回头对照成熟实现。

推荐节奏：

1. 读参考项目 README 和目录结构。
2. 不读实现，先写自己的接口草图。
3. 实现最小闭环。
4. 再读参考项目关键模块。
5. 写一篇“我原来哪里想浅了”的记录。

## Principle 2: 每个系统都要有可观测性

没有可观测性就没有真正理解。toy 项目也必须有：

- debug log
- state dump
- visualization
- deterministic replay
- benchmark
- failure corpus

toy OS 要能 dump page table；toy DB 要能打印 B+Tree；toy physics 要能画 contact manifold；toy agent 要能回放每次工具调用和上下文裁剪。

## Principle 3: Codex 是研究助理，不是代写员

这个仓库的 Codex 用法应该更像实验室搭档：

- 让 Codex 读陌生仓库并画模块图。
- 让 Codex 针对你的实现做 code review。
- 让 Codex 生成 property tests 和 fuzz cases。
- 让 Codex 对比两个设计方案的 failure modes。
- 让 Codex 帮你写“下一步实验计划”。

但核心代码最好由你自己敲。敲的过程会暴露你真正没懂的地方。

## Project Rhythm

每个项目都保留四类记录：

- `notes/<project>/reading.md`: 参考项目阅读笔记
- `notes/<project>/design.md`: 自己的设计取舍
- `notes/<project>/debug-log.md`: bug、假设、修复过程
- `notes/<project>/retrospective.md`: 阶段复盘

每完成一个 milestone，至少写一段：

```text
我现在能解释什么？
我还只能凭感觉操作什么？
下一个实验要验证什么？
```
