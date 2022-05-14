### IO流

- 输入流：把数据从`其他设备`上读取到`内存`中的流
- 输出流：把数据从`内存`中写出到`其他设备`上的流
- 字符流：以字节为单位，读写数据的流
- 字符流：以字符为单位，读写数据的流

|        | 输入流                    | 输出流                     |
| ------ | ------------------------- | -------------------------- |
| 字节流 | 字节输入流    InputStream | 字节输出流    OutputStream |
| 字符流 | 字符输入流    Reader      | 字符输出流    Writer       |

- 一切皆为字节

- `FileOutputStream`：文件字节输出流
  作用：把内存的数据写入到硬盘的文件中
  
- 写入数据的原理（内存 --> 硬盘）
  java程序 --> JVM(java虚拟机) --> OS（操作系统）--> OS调用写数据的方法 --> 把数据写入文件中
  
- 字节输出流的使用步骤（重点）：
  1. 创建一个FileOutputStream对象，构造方法中传递写入数据的目的地
  2. 调用FileOutputStream对象的方法write，把数据写入文件中(写数据的时候，会把十进制的整数转换为二进制整数)
  3. 释放资源（流使用会占用一定的内存，使用完毕要把内存清空，提高程序的效率）
  
- 任意的文本编辑器(记事本，notepad++......)
  在打开任意文本的时候，都会查询编码表，把字节转换为字符表示
  0-127:查询ASCII表
  其他值：查询系统默认码表(中文系统GBK)

- `public void write(byte[] b)`：将b.length字节从指定的字节数组写入此输出流
  一次写入多个字节：
      如果写的第一个字节是正数(0-127)，那么显示的时候会查询ASCII表
      如果写的第一个字节是负数，那第一个字节会和第二个字节，两个字节组成一个中文显示，查询默认系统码表(GBK)
  写入字符的方法：可以使用String类中的方法把字符串转换为字符数组
  `byte[] getBytes()`： 把字符串转化为字节数组

- 追加/续写
  ![1610853915864](C:\Users\12743\AppData\Roaming\Typora\typora-user-images\1610853915864.png)

  写换行：写换行符号
  windows： \r\n
  linux:    /n
  mac:    /r

- 读取数据原理（硬盘 --> 内存）
  java程序 --> JVM(java虚拟机) --> OS（操作系统）--> OS调用读取数据的方法 --> 读取文件

- 字节输入流的使用步骤（重点）

  1. 创建FileInputStream对象，构造方法中绑定要读取的数据源
  2. 使用FileInputStream对象中的方法read，读取文件
  3. 释放资源

- int read()读取文件中的一个字节并返回，读取到文件的末尾返回-1

- 字节输入流一次读取多个字节的方法
     int read(byte[] b)    从输入流中读取一定数量的字节，并将其储存在缓冲区的数组b中
      明确两件事情：

  1. 方法的参数byte[]的作用
         起到缓冲作用，存储每次读取到的多少字节
  2. 方法的返回值int
         每次读取的有效字节个数

- 同时使用读写的时候，在释放资源的时候，要先关闭写的，再关闭读的，如果写完了，肯定读完了

- 使用字节流读取中文文件
  1个中文：GBK占用两个字节，UTF-8占用3个字节

- 字符输入流的使用步骤

  1. 创建FileReader对象，构造方法中绑定要读取的数据源
  2. 使用FileReader对象中的read方法读取文件
     1. int read() 读取单个字符并返回
     2. int read(char[] cbuf) 一次读取多个字符，字符读入数组
     3. 释放资源

- 字符输出流的使用步骤（重点）

  1. 创建FileWriter对象，构造方法中绑定要写入的数据的目的地
  2. 使用FileWriter中的方法writer，把数据写入到内存缓冲区中（字符转换为字节的过程）
  3. 使用FileWriter中的flush，把内存缓冲区中的数据，刷新到文件中
  4. 释放资源（会先把内存缓冲区的数据刷新到文件中）

  - flush和close方法的区别：
    - flush：刷新缓冲区流对象可以继续使用
    - close：先刷新缓冲区，然后通知系统释放资源，流对象不可以再被使用了

- 字符输出流写数据的方法

  - `void write(int c)` 写入单个字符
  - `void writer(char[]) chuf)` 写入字符数组
  - `void writer(char[], int off, int len)` 写入字符数组的某一部分
  - `void writer(String str)` 写入字符串
  - `void writer(String str, int off, int len)` 写入字符串的某一部分。off字符串的开始索引，len写的是字符个数

- IO异常的处理
  jdk1.7以前，通过try catch finally来处理异常

  jdk7的新特性:
      在try的后边可以增加一个()，在括号中可以定义流对象，那么这个流对象的作用域就在try中有效

  ~~~java
  try(定义流对象；定义流对象...){
      可能产生异常的代码
  }catch(异常类变量 变量名){
      异常处理逻辑
  }
  ~~~

  

  ​    try中的代码执行完毕，会自动把流对象释放，不用写finally
  jdk9新特性：
  ​      在try前面可以定义流对象，在try后边的()中可以直接引入流对象的名称（变量名），在try代码执行完毕后，流对象也可以释放掉，不用写finally

  ~~~java
  A a = new A();
  B b = new B();
  try(a;b){
      可能会出现异常的代码
  }CATCH(异常变量名 变量名){
      异常处理逻辑
  }
  ~~~

- ![1610870820908](C:\Users\12743\AppData\Roaming\Typora\typora-user-images\1610870820908.png)

- ![1610870959457](C:\Users\12743\AppData\Roaming\Typora\typora-user-images\1610870959457.png)

- ![1610871449342](C:\Users\12743\AppData\Roaming\Typora\typora-user-images\1610871449342.png)

- ![1610872318626](C:\Users\12743\AppData\Roaming\Typora\typora-user-images\1610872318626.png)
- ![1610873849425](C:\Users\12743\AppData\Roaming\Typora\typora-user-images\1610873849425.png)

- ![1610874294805](C:\Users\12743\AppData\Roaming\Typora\typora-user-images\1610874294805.png)

  ![1610874357314](C:\Users\12743\AppData\Roaming\Typora\typora-user-images\1610874357314.png)

