使用位于虚拟机的方法区([§2.5.4](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-2.html#jvms-2.5.4)) 中的构造方法创建由N表示的类或接口C特定于实现的内部实现。类的创建可以被其他的类触发，例如被在运行时常量池中引用到C的类D。在D类中间接的调用C的方法也可以触发C的创建，例如反射([§2.12](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-2.html#jvms-2.12)) 。

如果C不为数组类，通过被类加载器加载其二进制表示所创建（[§4 (*The `class` File Format*](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html))。数组类没有外部的二进制形式；它们是由Java虚拟机而不是由类加载器创建的。

类加载器分为两种：jvm提供的启动类加载器和用户定义的类加载器。没一个用户定义的类加载器都是抽象类ClassLoader的子类。应用程序使用用户定义的类加载器，以扩展Java虚拟机动态加载并由此创建类的方式。用户定义的类加载器可用于创建源自用户定义的源的类。例如，可以通过网络下载类，动态生成类或从加密文件中提取类。

类加载器L可以通过直接定义C或委派给另一个类加载器来创建C。如果L直接创建C，我们说L定义了C，或者说L是C的定义加载器。

当一个类加载器委托给另一个类加载器时，启动加载过程的加载器不必与完成加载并定义类的加载器相同。如果L创建了C，无论其直径创建还是委托，我们认为L启动了C的加载，或者等效地，L是C的启动加载器。

在运行时，类或接口不是仅由其名称确定的，而成对使用：其二进制名称 ([§4.2.1](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-4.html#jvms-4.2.1)) 及其定义的类加载器。每个此类或接口都属于一个运行时包。类或接口的运行时程序包由程序包名称和定义该类或接口的类加载器确定。

Java虚拟机使用以下三个过程之一来创建由N表示的类或接口C：

- 如果N表示非数组类或接口，则使用以下两种方法之一来加载并由此创建C：
  - 如果D由引导类加载器定义，则引导类加载器将启动C的加载 ([§5.3.1](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-5.html#jvms-5.3.1)）。
  - 如果D是由用户定义的类加载器定义的，则该用户定义的类加载器将启动C的加载（第5.3.2节）。
- 否则，为N数组类。数组类是直接由Java虚拟机 ([§5.3.3](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-5.html#jvms-5.3.3))而不是由类加载器创建的。但是，在创建数组类C的过程中会使用D的定义类加载器。

**如果在类加载期间发生错误，则必须在程序中某个点（直接或间接）使用要加载的类或接口的位置上抛出LinkageError子类的实例。**

**如果Java虚拟机曾经尝试在验证 ([§5.4.1](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-5.html#jvms-5.4.1)) 或解析([§5.4.3](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-5.html#jvms-5.4.3))（而不是初始化 ([§5.5](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-5.html#jvms-5.5))期间加载类C，并且用于启动C加载的类加载器会抛出ClassNotFoundException的实例，那么Java虚拟机必须抛出NoClassDefFoundError实例，其原因是ClassNotFoundException实例。**

**（这里的一个微妙之处是，作为解析的一部分执行了递归类加载以加载超类（[§5.3.5](https://docs.oracle.com/javase/specs/jvms/se12/html/jvms-5.html#jvms-5.3.5), 步骤3）。因此，由于类加载器无法加载超类而导致的ClassNotFoundException必须包装在NoClassDefFoundError中。）**

行为良好的类加载器应维护三个属性：

- 给定相同的名称，好的类加载器应始终返回相同的Class对象。
- 如果类加载器L1将类C的加载委托给另一个加载器L2，那么对于任何以C的直接超类或直接超接口出现的类型T，或作为C中字段的类型，或作为C中方法或构造函数的形式参数的类型，或作为C中方法的返回类型，L1和L2应该返回相同的Class对象。
- 如果用户定义的类加载器预取了类和接口的二进制表示形式，或将一组相关的类一起加载，那么它必须仅在程序中不进行预取或组加载发生的点上反映加载错误。

我们有时会使用符号<N，L<sub>d</sub>>表示一个类或接口，其中N表示类或接口的名称，而L<sub>d</sub>表示类或接口的定义加载程序。

我们还将使用符号N<sup>Li</sup>表示类或接口，其中N表示类或接口的名称，而Li表示类或接口的启动加载程序。

