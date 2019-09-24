> *aconst_null*

**操作**

​	压入null

**格式**

> *aconst_null*

**形式**

*aload* = 25 (0x19)

**操作数栈**

... →

..., *objectref*

**描述**

Index是一个无符号字节，必须是当前帧的局部变量数组的索引([§2.6](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-2.html#jvms-2.6))。位于索引处的局部变量必须包含一个引用。索引处的局部变量中的objectref被压入操作数堆栈。

**注意**

与astore指令 ([§*astore*](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-6.html#jvms-6.5.astore)) 不同，aload指令不能用于将类型为returnAddress的值从局部变量加载到操作数栈中。

可以将aload操作码与wide指令([§*wide*](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-6.html#jvms-6.5.wide)) 结合使用，以使用两字节无符号索引访问局部变量。