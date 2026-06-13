# Tiny Coding Agent

目标：实现一个微小 Claude Code：能读仓库、制定计划、调用工具、编辑文件、运行测试、管理上下文，并能解释每一步为什么做。

参考项目：

- Aider: https://github.com/Aider-AI/aider
- SWE-agent: https://github.com/SWE-agent/SWE-agent
- OpenHands: https://github.com/All-Hands-AI/OpenHands
- OpenAI Codex CLI: https://github.com/openai/codex
- smolagents: https://github.com/huggingface/smolagents

## Milestones

### M1: Harness Skeleton

实现：

- conversation loop
- model client abstraction
- tool registry
- shell tool
- file read tool
- patch tool
- transcript log

必须能解释：

- agent 和普通 chat wrapper 的区别是什么？
- 工具调用失败如何进入下一轮推理？
- 为什么 transcript 是调试生命线？

### M2: Repo Awareness

实现：

- `rg` based file discovery
- context packing
- relevance scoring
- editable file set
- diff summary

Codex 任务：

```text
请审查我的 context packing 策略。
重点找：重要文件遗漏、重复内容浪费 token、旧上下文污染、用户最新请求被覆盖。
```

### M3: Planner And Executor

实现：

- task plan
- step status
- tool result summarization
- retry policy
- stop conditions

必须能解释：

- plan 什么时候有用，什么时候只是噪声？
- agent 如何避免无限循环？
- 什么情况下应该问用户？

### M4: Editing Discipline

实现：

- patch-only edits
- dirty worktree detection
- test runner
- lint runner
- rollback strategy

重点不是“能改文件”，而是“知道什么时候不该改”。

### M5: Evaluation

实现：

- small coding benchmark
- golden transcripts
- tool-call metrics
- failure taxonomy

## Completion

完成时你应该能解释：coding agent 的核心不是模型本身，而是 harness：上下文选择、工具边界、权限、可恢复编辑、反馈循环、用户意图对齐。
