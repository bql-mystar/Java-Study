- 可以通过重写toString方法来指定返回字符串

- equals方法：

  1. 基本数据类型：比较的是值

     引用数据类型：比较的是两个对象的地址值

  2. 可以用过重写equals方法比较两个对象的属性

  3. 在重写equals方法的过程中隐含了一个多态：
     多态的弊端：无法使用子类特有的内容（属性和方法）
     如： `Object obj = new Person("迪丽热巴", 19);`

     解决：可以使用向下转型，把obj类型转换为Person

  4. Objects类的equals方法：对两个对象进行比较，防止空指针异常

     ~~~java
     public static boolean equals(Object a, Object b){
         return (a == b || (a != null && a.equals(b)));
     }
     ~~~

     如果直接调用`eqals`方法的对象为null值的话，就会报空指针异常的错，通过`Object.equals`的话就可以避免这个问题