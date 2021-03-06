# C++语言的设计和演化

## 枚举

枚举本身在c++中是被视为一个单独的类型

```c++
  
  enum tt {a,b,c};
  enum ts {e,w,q};
  void h()                                                                            
  {
      // 枚举类型在实际应用中，视为一个单独类型，不可以由int类型直接初始化
      //tt t = 2;
          
     tt t = tt(2);
     int i = c;
  }
  
  void g(enum tt* pc, enum ts* pv) 
  {
      // 不同的枚举类型视为不同的类型，不能直接赋值
      //pc = pv;
  }

```



枚举是用户定义的一个单独类型

可以基于枚举进行运算符重载





## const

const 用于明确说明和限定函数或者对象从构建完成到析构的生命周期里是不变的这一原则

在对类的成员函数做const限定的实现原理是对this指针进行const限定。

与之对应的为**mutable**

mutable关键字的目的是突破const函数的限定，在const函数中可以进行状态无关的修改操作

## 静态成员函数

类的`static`数据成员是这样的一种成员，它只存在一个唯一的拷贝，而不像其他成员那样在每个对象中俄有一个拷贝。

* 不需要引用特定的对象就可以访问static成员。
* static成员可以用于减少全局名字的数量，可以把某个static成员逻辑上属于哪个类的问题弄明确
* 能实现对这些名字的访问控制
* 优点
  * 防止对全局命名空间的污染
  * 可以简化库代码的书写
  * 使同时使用多个库变得更加安全

