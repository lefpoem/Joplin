# 第十三章 int指令

1.int指令引发的中断，指令格式：int n,n为中断类型码，功能：引发中断过程。相当于引发一个n号中断的中断过程：取中断类型码n;标志寄存器入栈，IF=O，TF=0；CS，IP入栈；(IP)=(nx4),(CS)=(nx4+2)
2.中断处理程序可简称为中断例程。
3.ROM中存放着一套程序，称为BIOS（基本输入输出系统），BIOS有以下几部分内容：硬件系统的检测和初始化程序；外部中断和内部中断的中断例程；用于对硬件设备进行I/0操作的中断例程；其他和硬件系统相关的中断例程。
4.BIOS开机即执行安装程序，将中断向量写入到中断向量表中。FFFF：0处有一个跳转指令。
5.mov ax,4c00  分为两步mov ah,4ch(程序返回);mov al,0(返回值) int 21h含义为调用第21h号中断例程的4ch号子程序，功能为程序返回；
6.BIOS提供int 10h,int 21h,int 19h
