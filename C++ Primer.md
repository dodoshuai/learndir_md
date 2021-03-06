## C++ Primer

* 变量初始化规则

  * 内置类型变量是否自动初始化取决于内置类型变量定义的位置。
    * 在函数体外定义的变量都初始化成0
    * 在函数体里定义的内置类型变量不进行自动初始化
  * 类类型变量的初始化
    * 构造函数和默认构造函数（default constructor）

* 声明和定义

  * 声明：用于向程序表明变量的类型和名字。
  * 定义：用于为变量分配存储空间，还可以为变量指定初始值。

* const限定符

  * 魔数：其本身的意义在上下文中没有体现出来。好想这个数是魔术般地从空中出现的。增强程序可读性。
  * const对象默认为文件的局部变量
  * 非const变量默认为extern。要使用const变量能够在其他的文件中访问，必须显式指定它为extern。

* typedef名字

  * 为了隐藏特定类型的实现，强调使用类型的目的。
  * 简化复杂的类型定义，使其更容易理解。
  * 允许一种类型用于多个目的，同时使得每次使用该类型的目的明确。

* enum枚举

  * 每个enum都定义了一种唯一的类型
  * 枚举成员值可以是不唯一的
  * 枚举成员是常量

* 类型转换

  * 如果两个类型之间可以相互转换，则称这两个类型相关。
  * 何时发生隐式类型转换
    * 在混合类型的表达式中，其操作数被转换为相同的类型
    * 用作条件的表达式被转换为bool类型
    * 用一表达式初始化某个变量或将一表达式赋值给某个变量，则该表达式被转换为该变量的类型
  * 算术转换
    * 有符号与无符号类型之间的转换
  * 其他隐式转换
    * 指针转换
    * 转换为bool类型
    * 算术类型于bool类型的转换
    * 转换与枚举类型（枚举类型使用方式参照枚举定义）
    * 转换为const对象（使用非const对象初始化const对象时）
    * 由标准库类型定义的转换

* 指针的引用

  引用不是对象，因此不能定义引用的指针。之真实对象，因而可以定义指针的引用。

  ```c++
  int i = 42;
  int *p;
  int *&r = p;
  r = &i;	// &i 赋值给 r,是的 p 指向 i
  *r = 0;	// 解引用 r 返回 i 变量， 从而将 0 赋值给 i 变量
  ```

   r is a referrence to a pointer to an int;

* 8.5 导致下面的while终止的原因是：if 判断的是流状态，while检测的是条件表达式返回的流，从而间接地检查了流的状态。

  ```C++
  while(cin >> i) /*...*/ //
  ```

* 程序使用动态内存通常出于以下三种原因之一：

  * 不确定需要使用多少对象
  * 不确定所需对象的准确类型
  * 需要在多个对象间共享数据

* 什么是智能指针：智能指针可以辅助用户进行动态内存管理，它可以自动释放所指向的对象

* 关系容器以及某些算法，使用默认<操作符。一般而言，关系操作符，诸如相等操作符，应定义为非成员函数。

* 赋值操作符可以重载。无论形参为何种类型，赋值操作符必须定义为成员函数，这一点与复合赋值操作符有所不同。

* 类定义下标操作符时，一般需要定义两个版本：一个为非const成员并返回引用，另一个为const成员并返回const引用。

* 重载箭头操作符必须返回指向类类型的指针，或者返回定义了自己的箭头操作符的类类型对象。

* **虚函数**是动态绑定，缺省参数是静态绑定的，调用指针是哪种类型，就使用该类型对应的类中该函数定义时的缺省值。

---

### 建议

1. 建议每个内置类型的对象都要初始化。虽然这样做并不总是必须的，但是会更加容易和安全，除非你确定忽略初始化不会带来风险。
2. 常量确定以后就不能被修改所以定义是必须初始化。
3. 