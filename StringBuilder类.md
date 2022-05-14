## StringBuilder类

- String类：

  1. 字符串是常量，他们的值在创建之后不能更改

  2. 字符串的底层是一个被final修饰的数组，不能改变，是一个常量

  3. 进行字符串的相加，内存中就会有对个字符串，占用空间多，效率低下，举例如下：

     ~~~java
     String s = "a" + "b" + "c"; //"abc"
     /* 在这个拼接过程中，会先创建三个字符串，分别为"a","b","c",然后"a"和"b"相加得到字符串"ab",又创建了一个新的字符串，然后"ab"和"c"相加得到字符串"abc"，这个过程中就产生了五个字符串 */
     ~~~

     

- StringBuilder(字符串缓冲区)，可以提高字符串的操作效率（看成一个长度可以变化的字符串）
  底层也是一个（长度为16）数组，但是没有被final修饰，可以改变长度

- StringBuilder在内存中始终是一个数组，占用空间少，效率高

- 如果超出了StringBuilder的容量，会自动的扩容

- StringBuilder常用方法：

  1. append():
     使用append方法往StringBuilder中添加数据
     append方法返回的是this，也就是调用方法的对象本身
     使用append方法无需接收返回值
  2. StringBuilder和String可以相互转换：
     String -> StringBuilder：可以使用StringBuilder的构造方法
             StringBuilder(String str) 构造一个字符串生成器，并初始化指定的字符串内容
     StringBuilder -> String：可以使用StringBuilder的toString方法