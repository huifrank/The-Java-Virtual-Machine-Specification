> ***aastore***

**操作**

存储进引用数组中

**格式**

```
aastore
```

**形式**

*aastore* = 83 (0x53)

**操作数栈**

..., *arrayref*, *index*, *value* →

...

**描述**

arrayref必须为引用类型，切其指向的数组元素也必须是引用类型。index必须为int类型，value必须为引用类型。arrayref,index,value位于操作数栈中，在使用时会弹出。

如果value为null，其也将做为数据存储在对应位置。

如果value不为null，如果值的类型与arrayref引用的数组的元素类型兼容，则value也将存储在数组对应位置。

以下规则将用于确认value类型是否与数组元素类型兼容。定义S为value所引用对象的类型，T为数组元素的类型：

- 如果S为class类型：
  - 如果T为class类型，则S必须与T类型相同，或S为T的子类。
  - 如果T为interface类型，则S必须实现了接口T。
- 如果S为数组类型SC[] ，即数组元素类型为SC：
  - 如果T为class类型，这T必须是Object。
  - 如果T为interface类型，则T必须数组实现的其中一个接口(JLS §4.10.3)
  - 如果T是数组类型TC []，即TC类型的组件数组，则必须满足以下条件之一：
    - TC和SC是相同的原始类型。
    - TC和SC是引用类型，SC类型可通过这些运行时规则分配给TC。

**运行时异常**

**如果arrayref为null，aastore会抛出NullpointerException**

**或者，如果index不在arrayref引用的数组范围内，则aastore指令会抛出ArrayIndexOutOfBoundsException。**

**如果arrayref不为null且非null值的实际类型与数组的元素的实际类型不兼容，则aastore会抛出ArrayStoreException。**