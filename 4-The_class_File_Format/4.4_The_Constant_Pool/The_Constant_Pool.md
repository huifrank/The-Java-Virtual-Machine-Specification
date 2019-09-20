Java虚拟机指令不依赖于类，接口，类实例或数组的运行时布局。相反，JVM指令依赖的是constant_pool表中的符号信息。

所有的常量元素都为以下格式：

```c
cp_info {
    u1 tag;
    u1 info[];
}
```

constant_pool表中的每个条目必须以1字节标记开头，表示条目的常量类型。表[Table 4.4-A](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.4-140)按章节顺序列出了17种常量及其对应的标记。每个标记字节后面必须跟有两个或多个字节，提供有关该常量的信息。其附加信息的格式取决于不同的tag标记字节。也就是说，info数组的内容随tag的值而变化。

**Table 4.4-A. Constant pool tags (by section)**

| Constant Kind                 | Tag  | Section                                                      |
| ----------------------------- | ---- | ------------------------------------------------------------ |
| `CONSTANT_Class`              | 7    | [§4.4.1](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.4.1) |
| `CONSTANT_Fieldref`           | 9    | [§4.4.2](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.4.2) |
| `CONSTANT_Methodref`          | 10   | [§4.4.2](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.4.2) |
| `CONSTANT_InterfaceMethodref` | 11   | [§4.4.2](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.4.2) |
| `CONSTANT_String`             | 8    | [§4.4.3](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.4.3) |
| `CONSTANT_Integer`            | 3    | [§4.4.4](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.4.4) |
| `CONSTANT_Float`              | 4    | [§4.4.4](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.4.4) |
| `CONSTANT_Long`               | 5    | [§4.4.5](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.4.5) |
| `CONSTANT_Double`             | 6    | [§4.4.5](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.4.5) |
| `CONSTANT_NameAndType`        | 12   | [§4.4.6](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.4.6) |
| `CONSTANT_Utf8`               | 1    | [§4.4.7](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.4.7) |
| `CONSTANT_MethodHandle`       | 15   | [§4.4.8](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.4.8) |
| `CONSTANT_MethodType`         | 16   | [§4.4.9](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.4.9) |
| `CONSTANT_Dynamic`            | 17   | [§4.4.10](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.4.10) |
| `CONSTANT_InvokeDynamic`      | 18   | [§4.4.10](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.4.10) |
| `CONSTANT_Module`             | 19   | [§4.4.11](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.4.11) |
| `CONSTANT_Package`            | 20   | [§4.4.12](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.4.12) |

在版本号为v的类文件中，constant_pool表中所出现的tag值必须是首次在类文件格式 ([§4.1](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.1))版本v或更早版本中定义的标记。也就是说，每个条目必须表示一种被批准在类文件中使用的常量。表 [Table 4.4-B](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.4-210) 列出了每个标记，以及定义它的类文件格式的第一个版本。

**Table 4.4-B. Constant pool tags (by tag)**

| Constant Kind                 | Tag  | `class` file format | Java SE |
| ----------------------------- | ---- | ------------------- | ------- |
| `CONSTANT_Utf8`               | 1    | 45.3                | 1.0.2   |
| `CONSTANT_Integer`            | 3    | 45.3                | 1.0.2   |
| `CONSTANT_Float`              | 4    | 45.3                | 1.0.2   |
| `CONSTANT_Long`               | 5    | 45.3                | 1.0.2   |
| `CONSTANT_Double`             | 6    | 45.3                | 1.0.2   |
| `CONSTANT_Class`              | 7    | 45.3                | 1.0.2   |
| `CONSTANT_String`             | 8    | 45.3                | 1.0.2   |
| `CONSTANT_Fieldref`           | 9    | 45.3                | 1.0.2   |
| `CONSTANT_Methodref`          | 10   | 45.3                | 1.0.2   |
| `CONSTANT_InterfaceMethodref` | 11   | 45.3                | 1.0.2   |
| `CONSTANT_NameAndType`        | 12   | 45.3                | 1.0.2   |
| `CONSTANT_MethodHandle`       | 15   | 51.0                | 7       |
| `CONSTANT_MethodType`         | 16   | 51.0                | 7       |
| `CONSTANT_Dynamic`            | 17   | 55.0                | 11      |
| `CONSTANT_InvokeDynamic`      | 18   | 51.0                | 7       |
| `CONSTANT_Module`             | 19   | 53.0                | 9       |
| `CONSTANT_Package`            | 20   | 53.0                | 9       |

constant_pool表中的某些条目是可加载的，因为他们可以在运行时压入堆栈以供进一步计算使用。在版本号为v的类文件中，如果constant_pool表中的条目为首次被认为可在版本v或更早版本中加载的标记，则该条目是可加载的。表 [Table 4.4-C](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.4-310) 列出了每个标记首个被认为是可加载的Java SE版本。还显示了Java SE引入了该类文件格式的版本。

*在除CONSTANT_Class之外的情况下，首个定义该标签的类文件格式于首个可加载该标签的Java SE为同一个版本。*

**Table 4.4-C. Loadable constant pool tags**

| Constant Kind           | Tag  | `class` file format | Java SE |
| ----------------------- | ---- | ------------------- | ------- |
| `CONSTANT_Integer`      | 3    | 45.3                | 1.0.2   |
| `CONSTANT_Float`        | 4    | 45.3                | 1.0.2   |
| `CONSTANT_Long`         | 5    | 45.3                | 1.0.2   |
| `CONSTANT_Double`       | 6    | 45.3                | 1.0.2   |
| `CONSTANT_Class`        | 7    | 49.0                | 5.0     |
| `CONSTANT_String`       | 8    | 45.3                | 1.0.2   |
| `CONSTANT_MethodHandle` | 15   | 51.0                | 7       |
| `CONSTANT_MethodType`   | 16   | 51.0                | 7       |
| `CONSTANT_Dynamic`      | 17   | 55.0                | 11      |

