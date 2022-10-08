# HUST-RiscV-CPU-Design


[TOC]
## Lab-1 单周期处理器， 差异化指令CCAB

**问题记录**
- **[Solved]** `SB`指令的实现较为复杂。由于数据存储器只能按双字对齐寻址，故需要先加载整个双字，替换掉其中一个字节再写入存储器
- **[Fixed]** RiscV手册里的立即数`[20:1]`，最初被我理解成20位`[19:0]`并据此实现，引发一系列错误并在单条`branch`指令上陷入死循环

## Lab-2 流水线处理器

### 理想流水线

**问题记录**

- **[Fixed]** 在单周期中实现的`ecall`触发`halt`的电路未锁存，导致在流水线中`ecall`失效
- **[Fixed]** 写目标寄存器时直接使用了ID段的目标寄存器，应使用WB段的

### 气泡流水线

**问题记录**

- **[Fixed]** 寄存器文件改为下降沿
- **[Fixed]** benchmark出了点错误，调了很久没通过测试
- **[Solved]** 为了处理ecall指令，需用halt改变时钟源部分的逻辑，使得ecall退出时，时钟**一直维持**在**高电平**，流水线不工作，并且恢复后寄存器正常写入此时的数据