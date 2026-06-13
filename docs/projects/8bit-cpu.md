# 8-bit CPU

目标：按照 Ben Eater 路线搭一个 8-bit breadboard CPU，同时用 Logisim/Nand2Tetris 补上抽象层。

参考项目：

- Ben Eater 8-bit computer: https://eater.net/8bit
- Nand2Tetris projects: https://github.com/nand2tetris/projects
- Logisim Evolution: https://github.com/logisim-evolution/logisim-evolution

## Milestones

### M1: Digital Logic Warmup

实现或验证：

- NAND/NOR/XOR
- half adder/full adder
- latch/flip-flop
- register
- counter

必须能解释：

- 组合逻辑和时序逻辑的区别
- clock edge 为什么重要
- floating input 为什么危险

### M2: Datapath

搭建：

- bus
- registers
- ALU
- flags
- program counter
- memory

Codex 任务：

```text
请帮我把当前 CPU datapath 画成模块表。
每个模块列出输入、输出、控制信号、时序约束、可能故障。
```

### M3: Control Unit

实现：

- instruction register
- microcode ROM
- control word
- fetch/decode/execute
- reset/step clock

### M4: ISA And Assembler

实现：

- instruction set
- assembly syntax
- assembler
- sample programs
- manual test ROM

### M5: Hardware Debugging

记录：

- oscilloscope/logic analyzer traces
- bad wiring cases
- unstable clock cases
- power/noise issues

## Completion

完成时你应该能解释：一条指令不是“CPU 执行了”，而是控制信号在多个 clock cycle 中驱动 datapath 状态转移。
