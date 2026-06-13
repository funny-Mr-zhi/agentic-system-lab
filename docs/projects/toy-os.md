# Toy OS

目标：实现一个小 kernel：能 boot、管理内存、调度任务、提供系统调用、读写简单文件系统。

参考项目：

- xv6: https://github.com/mit-pdos/xv6-public
- rCore Tutorial: https://github.com/rcore-os/rCore-Tutorial-v3
- blog_os: https://github.com/phil-opp/blog_os
- SerenityOS: https://github.com/SerenityOS/serenity

## Milestones

### M1: Boot

实现：

- bootloader path
- kernel entry
- VGA/serial output
- panic handler
- QEMU run script

必须能解释：

- CPU 从 reset 到 kernel entry 经历了什么？
- linker script 在控制什么？
- 为什么 serial log 比屏幕输出更适合调试？

### M2: Memory

实现：

- physical frame allocator
- virtual memory
- page table dump
- heap allocator

Codex 任务：

```text
请审查我的 page table 和 allocator。
重点找 alignment、double free、mapping flags、user/kernel isolation、panic 后可诊断性。
```

### M3: Interrupts And Syscalls

实现：

- IDT/trap vector
- timer interrupt
- keyboard/serial
- syscall ABI
- user/kernel transition

### M4: Multitasking

实现：

- process/thread struct
- context switch
- scheduler
- sleep/wakeup
- wait/exit

### M5: File System

实现：

- block device abstraction
- inode 或 extent
- directory
- file read/write
- simple shell

## Completion

完成时你应该能解释：kernel 是一组对硬件资源的受控抽象，核心工作是隔离、复用、命名、调度和恢复。
