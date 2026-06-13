# Git Workflow

这个仓库会长期承载八个从零手搓项目，所以 git 策略要同时满足两件事：

1. `main` 永远像一本能读的书。
2. `practice/` 和 `experiments/` 允许大胆试错。

## Branches

推荐保留三类分支。

### `main`

稳定主线，只放这些内容：

- 文档路线图
- 已完成 milestone 的代码
- 可复现的实验记录
- 重要复盘

`main` 不追求每次提交都完美，但每次提交应该能解释清楚“为什么存在”。

### `project/<name>-m<index>-<topic>`

项目 milestone 分支，例如：

```bash
git switch -c project/tiny-torch-m1-autograd
git switch -c project/database-m2-bptree
git switch -c project/coding-agent-m1-harness
```

适合持续几天到几周的真实实现。

### `exp/<name>-<idea>`

短命实验分支，例如：

```bash
git switch -c exp/db-copy-on-write-pages
git switch -c exp/agent-context-packer
git switch -c exp/physics-solver-warm-start
```

实验分支可以乱一点，但合并前要写清楚结论：保留、丢弃，还是沉淀成文档。

## Versioning

这个仓库不适合传统产品版本号。推荐用 milestone tag。

格式：

```text
<project>/m<index>-<name>
```

例子：

```bash
git tag tiny-torch/m1-autograd
git tag database/m2-bptree
git tag coding-agent/m1-harness
git tag browser/m3-layout
```

如果某个 milestone 以后重写了，用递增后缀：

```bash
git tag tiny-torch/m1-autograd-v2
```

发布到远端：

```bash
git push origin tiny-torch/m1-autograd
git push origin --tags
```

## Commit Style

使用轻量 Conventional Commits，但 scope 用项目名或区域名。

格式：

```text
<type>(<scope>): <summary>
```

常用 type：

- `docs`: 文档、路线、笔记
- `feat`: 新功能或新 milestone 能力
- `test`: 测试、fixtures、fuzz cases
- `fix`: bug 修复
- `refactor`: 不改变行为的重构
- `exp`: 实验性改动
- `chore`: 仓库管理、配置、脚手架

例子：

```bash
git commit -m "docs(repo): add git workflow"
git commit -m "feat(tiny-torch): implement scalar value graph"
git commit -m "test(database): add btree split cases"
git commit -m "exp(agent): try simple relevance scorer"
git commit -m "refactor(browser): separate dom and layout nodes"
```

## Daily Commands

开始一个 milestone：

```bash
git switch main
git pull --ff-only
git switch -c project/tiny-torch-m1-autograd
```

查看当前变化：

```bash
git status --short
git diff
git diff --staged
```

分块提交：

```bash
git add -p
git commit -m "feat(tiny-torch): add scalar add and mul"
```

同步到 GitHub：

```bash
git push -u origin project/tiny-torch-m1-autograd
```

合并回主线：

```bash
git switch main
git pull --ff-only
git merge --no-ff project/tiny-torch-m1-autograd
git push origin main
```

打 milestone tag：

```bash
git tag tiny-torch/m1-autograd
git push origin tiny-torch/m1-autograd
```

## What To Commit

应该提交：

- 亲手写的实现
- 测试
- benchmark 脚本
- 小型 fixtures
- 阅读笔记
- 设计决策
- 复盘文档
- 可读的架构图源文件

不应该提交：

- 密钥和 token
- `.codex/`、`.claude/`、`.cursor/` 等本地 AI 工具状态
- 大型生成数据
- 编译产物
- 虚拟环境
- 本地 kubeconfig
- Terraform state
- benchmark 输出大文件

如果某个大文件确实是长期资产，用 Git LFS，不要直接塞进普通 git history。

## Notes Discipline

每个 milestone 至少配一条笔记提交。

推荐节奏：

```bash
git commit -m "docs(database): record btree split design"
git commit -m "feat(database): implement leaf split"
git commit -m "test(database): add randomized insert oracle"
git commit -m "docs(database): write m2 retrospective"
```

这样未来回看时，你不仅能看到“代码变了”，还能看到“理解怎么变了”。

## Agent Safety

使用 Codex、Claude Code、Aider 等工具时，建议先提交一个干净基线：

```bash
git status --short
git add -A
git commit -m "chore(repo): checkpoint before agent session"
```

让 agent 改完后先审查：

```bash
git diff
git diff --stat
```

满意后再提交：

```bash
git add -p
git commit -m "feat(agent): describe the actual change here"
```

不要把 agent transcript、临时上下文、工具日志提交进仓库。真正有学习价值的内容，整理后写进 `notes/`。

## First Commit

如果这是新仓库，推荐第一组提交这样做：

```bash
git add README.md init.md docs practice notes experiments assets .gitignore LICENSE
git commit -m "docs(repo): initialize agentic systems lab"
git branch -M main
git remote add origin git@github.com:<your-name>/agentic-systems-lab.git
git push -u origin main
```

如果远端已经存在，跳过 `remote add`，改用：

```bash
git remote -v
git push -u origin main
```
