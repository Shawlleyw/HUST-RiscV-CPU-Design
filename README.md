# HUST-RiscV-CPU-Design


[TOC]
## Lab-1 Single Cycle Processor with CCAB

**问题记录**
- [Solved] `SB`指令的实现较为复杂。由于数据存储器只能按双字对齐寻址，故需要先加载整个双字，替换掉其中一个字节再写入存储器
- [Fixed] RiscV手册里的立即数`[20:1]`，最初被我理解成20位`[19:0]`并据此实现，引发一系列错误并在单条`branch`指令上陷入死循环

