> **aaload**

**操作**

从数组中加载引用

**格式**

```
aaload
```

**形式**

*aaload* = 50 (0x32)

**操作数栈**

..., *arrayref*, *index* →

..., *value*

**描述**

arrayref必须是类型引用，并且必须引用其组件类型为reference的数组。index必须是int类型，arrayref和index都从操作数堆栈中弹出。取出数组索引处元素的引用值将其推送到操作数栈。

**运行时异常**

**如果arrayref为null，则aaload会抛出NullPointerException。**

**否则，如果index不在arrayref引用的数组范围内，则aaload指令会抛出ArrayIndexOutOfBoundsException。**

