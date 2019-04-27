JVM支持的原始数据类型有数字类型，布尔类型 ([§2.3.4](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-2.html#jvms-2.3.4))和返回地址类型(returnAddress [§2.3.3](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-2.html#jvms-2.3.3))。

数字类型包括整体类型型( *integral types* [§2.3.1](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-2.html#jvms-2.3.1))和浮点型( *floating-point types* [§2.3.2](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-2.html#jvms-2.3.2))。

整体类型有:

* byte 其值为8位有符号的二进制补码整数。默认值是0
* short 其值为8位有符号的二进制补码整数。默认值是0
* int 其值为32位有符号的二进制补码整数。默认值是0
* long 其值为64位有符号的二进制补码整数。默认值是0
* char 其值为16位无符号整数，表示为Unicode编码，由UTF-16编码，默认值为null的代码点(`'\u0000'`)

浮点类型有：

* float 其值为浮点值集的元素集或浮点扩展指数（ float-extended-exponent）值集（如果支持），默认值为正零。
* double 其值为双精度浮点值集的元素集或双精度浮点扩展指数(double-extended-exponent)值集(如果支持)，默认值为正零。

布尔类型的值对true和false进行编码，默认值为false。

*Java®虚拟机规范的第一版没有将布尔值视为Java虚拟机类型。然而，布尔值在Java虚拟机中的支持有限，Java®虚拟机规范的第二版通过将布尔值视为一种类型来澄清该问题。*

returnAddress类型的值是指向Java虚拟机指令的操作码的指针。在原始类型中，只有returnAddress类型与Java编程语言类型没有直接关联。

