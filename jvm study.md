# jvm study

​	push ax 表示将寄存器ax的值存入栈中，栈指针向上移一个字；pop ax表示将栈顶的值存入ax中，栈指针向下移动一个字。 

​	AT&T汇编指令是从左往右赋值，例如

```assembly
movl $32h %ebp
```

将32h赋值给ebp寄存器的值存入ebp寄存器。

```assembly
pushl %ebp
```

将寄存器ebp的值压栈。

```assembly
popl %ebp
```

将栈顶的值压入epb寄存器。

事实上时代发生的发

威锋网