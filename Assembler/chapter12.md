# 第十二章 内中断

1.“中断信息”是要求CPU马上进行某种处理，并向所要进行的该种处理提供了必备参数的通知信息。
2.具体产生中断信息的有：除法错误，比如，执行div指令产生的除法溢出；单步执行；执行into指令；执行int（interrupt）指令
3.中断类型码为一个字节型数据，标识中断信息的来源。产生中断信息的事件，中断的来源称为中断源。
4.四种中断源的中断类型码分别为：除法错误：0；单步执行：1；执行into指令：4；执行int指令：int n,n为字节型立即数;
5.找到中断向量表成了通过中断类型码找到中断处理程序入口地址的先决条件。中断向量表保存在内存中。
6.8086CPU中断向量表放在0000：0000～0000：03FF单元中（硬性规定）。一个中断向量表项占两个字（4B）分别存放，段地址：偏移地址。高地址字存放段地址，低地址字存放偏移地址。共256个中断源所对应的中断入口地址。
7.用中断向量码找到中断向量，并用它设置CS和IP，此工作是由CPU的硬件自动完成的。此过程称为中断过程。
8.编写中断程序的方法：保存用到的寄存器；处理中断；恢复用到的寄存器；用iret指令返回。iret指令的功能描述为：pop IP pop CS popf
9.编译器支持：mov ax,8-4 等同于 mov ax,4即汇编编译器可以处理表达式。例：mov ax,(5+3)*5/10 处理为 mov ax,4
10.对ss:sp写入地址时不会引发中断，最好是连续存储。