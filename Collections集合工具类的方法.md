### Collections集合工具类的方法

- 要想调用sort方法，那么必须实现Comparable接口，并重写compareTo方法定义排序的规则

- Comparable接口的排序规则：
  自己（this）- 参数：升序
  参数 - 自己（this）： 降序

- 还有一个compare的重载方法

  `public static <T> void sort(list<T>, Comparator<? super T>)`:将集合元素按照指定规则排序

  - Comparator和Comparable的区别：
    Comparable：自己（this）和别人（参数）比较，自己需要实现Comparable接口，重写比较的规则compareTo方法
    Comparator：相当于找一个第三方的裁判，比较两个

  - Comparator的排序规则：
    o1 - o2：升序

    o2 - o1：降序