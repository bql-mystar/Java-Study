### transient:瞬态关键字

- static关键字：静态关键字
      	静态优先于非静态加载到内存中(静态优先于对象进入到内存中)

​        被static修饰的成员变量不能被序列化，序列化的都是对象

- transient:瞬态关键字

  ​        被transient关键字修饰的成员变量，不能被序列化 