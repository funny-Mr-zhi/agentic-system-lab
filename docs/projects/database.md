# Toy Database

目标：实现一个能持久化、能索引、能并发读写、能解释查询计划的小数据库。

参考项目：

- sqlite clone tutorial: https://github.com/cstack/db_tutorial
- BusTub: https://github.com/cmu-db/bustub
- MiniOB: https://github.com/oceanbase/miniob
- BoltDB: https://github.com/boltdb/bolt

## Milestones

### M1: Page And File

实现：

- fixed-size page
- pager
- table file
- row serialization
- insert/select

必须能解释：

- page size 为什么重要？
- disk layout 和 memory layout 哪里不同？
- crash 写到一半会怎样？

### M2: B+Tree

实现：

- leaf/internal node
- search
- insert
- split
- range scan
- tree dump

Codex 任务：

```text
请帮我审查 B+Tree split 逻辑。
重点找 key 顺序、parent pointer、root split、重复 key、range scan 边界。
```

### M3: Buffer Pool

实现：

- page cache
- pin/unpin
- dirty page
- LRU/K replacement
- flush

必须能解释：

- 为什么不能随便 evict pinned page？
- dirty page 什么时候落盘？
- buffer pool 如何影响查询性能？

### M4: Transactions

实现：

- read/write transaction
- WAL
- commit/rollback
- crash recovery
- simple locking

先做保守方案，不急着 MVCC。

### M5: Query Layer

实现：

- tokenizer/parser
- logical plan
- physical executor
- seq scan/index scan
- filter/project

## Experiments

- 随机 insert/delete，与 Python dict + sorted list 做 oracle 对照。
- crash 后重启，验证 committed 数据存在、uncommitted 数据消失。
- range scan benchmark。
- 热点 key 并发读写。

## Completion

完成时你应该能解释：数据库的复杂性不在“把数据写进文件”，而在持久化、缓存、索引、并发、恢复和查询执行之间的约束。
