# The-Java-Virtual-Machine-Specification

## java 虚拟机规范 se12 中文翻译

base on
https://docs.oracle.com/javase/specs/jvms/se12/html/index.html



## 1 Introduction  简介

- [关于java的一些历史](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/1-Introduction/1.1_A_Bit_of_History.md)
- [java虚拟机](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/1-Introduction/1.2_The_Java_Virtual_Machine.md)
- [此规范的结构](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/1-Introduction/1.3_Organization_of_the_Specification.md)
- [符号格式定义](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/1-Introduction/1.4_Notation.md)
- [反馈](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/1-Introduction/1.5_Feedback.md)

## 2 [Java虚拟机结构](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/2-The_Structure_of_The_Java_Virtual_Machine/The_Structure_of_the_Java_Virtual_Machine.md)

- [类文件格式](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/2-The_Structure_of_The_Java_Virtual_Machine/2.1_The_class_File_Format.md)

- [数据类型](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/2-The_Structure_of_The_Java_Virtual_Machine/2.2_Data_Types.md)

  ###  [基本数据类型](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/2-The_Structure_of_The_Java_Virtual_Machine/2.3_Primitive_Types_and_Values/Primitive_Types_and_Values.md)

  ​	[整型](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/maste	r/2-The_Structure_of_The_Java_Virtual_Machine/2.3_Primitive_Types_and_Values/2.3.1_Integral_Types_and_Values.md)

  ​	[浮点类型](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/2-The_Structure_of_The_Java_Virtual_Machine/2.3_Primitive_Types_and_Values/2.3.2_Floating-Point_Types_Value_Sets_and_Values.md)

  ​	[returnAddress类型](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/2-The_Structure_of_The_Java_Virtual_Machine/2.3_Primitive_Types_and_Values/2.3.3_The_returenAddress_Type_and_Values.md)

  ​	[布尔类型](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/2-The_Structure_of_The_Java_Virtual_Machine/2.3_Primitive_Types_and_Values/2.3.4_The_boolean_Type.md)

- [引用类型](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/2-The_Structure_of_The_Java_Virtual_Machine/2.4_Reference_Types_and_Values.md)

  ### [运行时数据区](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/2-The_Structure_of_The_Java_Virtual_Machine/2.5_Run-Time_Data_Areas/Run-Time_Data_Areas.md)

  [pc寄存器](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/2-The_Structure_of_The_Java_Virtual_Machine/2.5_Run-Time_Data_Areas/2.5.1_The_pc_Register.md)

  [虚拟机栈](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/2-The_Structure_of_The_Java_Virtual_Machine/2.5_Run-Time_Data_Areas/2.5.2_Java_Virtual_Machine_Stacks.md)

  [堆](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/2-The_Structure_of_The_Java_Virtual_Machine/2.5_Run-Time_Data_Areas/2.5.3_Heap.md)

  [方法区](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/2-The_Structure_of_The_Java_Virtual_Machine/2.5_Run-Time_Data_Areas/2.5.4_Method_Area.md)

  [运行时常量池](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/2-The_Structure_of_The_Java_Virtual_Machine/2.5_Run-Time_Data_Areas/2.5.5_Run-time_Constant_Pool.md)

  [本地方法栈](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/2-The_Structure_of_The_Java_Virtual_Machine/2.5_Run-Time_Data_Areas/2.5.6_Native_Method_Stacks.md)

  ### [帧](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/2-The_Structure_of_The_Java_Virtual_Machine/2.6_Frames/Frames.md)

  [局部变量表](https://github.com/huifrank/The-Java-Virtual-Machine-Specification/blob/master/2-The_Structure_of_The_Java_Virtual_Machine/2.6_Frames/2.6.1_Local_Variables.md)

  

