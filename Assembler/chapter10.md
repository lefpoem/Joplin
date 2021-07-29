# 第十章 CALL和RET指令

1.call和ret都是转移指令，都修改IP或者同时修改CS和IP
2.ret指令用栈中的数据，修改IP中的内容，从而实现近转移，pop IP 例子：函数的返回
3.retf指令用栈中的数据，同时修改CS：IP中的内容，从而实现远转移，先修改IP，再修改CS。pop IP,pop CS
4.call指令：将当前的IP或CS和IP压入栈中；转移。例子：函数的调用。call类似于jmp。call不能实现短转移。
5.**依据位移进行转移的call指令**16位近转移，格式：call 标号相当于：push IP;jmp near ptr 标号
6.**转移的目的地址在指令中的call指令**格式：call far ptr 标号实现的是段间转移。相当于：push CS;push IP;jmp far ptr 标号。
7.**转移地址在寄存器中的call指令**格式：call 16位 reg相当于：push IP,jmp 16 位reg
8.**转移地址在内存中的call指令**格式：call word ptr 内存单元地址相当于：push IP； jmp word ptr 内存单元地址，call dword ptr 内存单元地址相当于:push CS push IP jmp dword ptr 内存单元地址。
9.成对使用call ret可以将小程序返回。
10.mul乘法指令，要求：两个相乘的数必须位数相同，8位一个乘数默认在AL中；16位一个乘数默认在AX中。结果，如果8位乘法，结果默认放在AX中；如果16位乘法，高位放在DX中，低位放在AX中。格式：mul reg；mul 内存单元。
