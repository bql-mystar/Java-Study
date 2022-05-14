### Map

- Map集合的特点：

  1. Map集合是一个双列集合，一个元素包含两个值（一个key，一个value）
  2. Map集合中的元素，key和value的数据类型可以相同，也可以不同
  3. Map集合的元素，key是不允许重读的，value是可以重复的
  4. Map集合的元素，key和value是一一对应的

- HashMap的特点：

  1. HashMap实现了Map接口

  2. HashMap集合底层是哈希表：查询速度特别的快

     JDK1.8之前：数组 + 单向链表

     JDK1.8之后：数组 + 单向链表/红黑树（链表长度超过8）：提高查询的速度

  3. HashMap集合是一个无序的集合，存储元素和取出元素的顺序有可能不一致

- LinkedHashMap的特点：

  1. LinkedHashMap继承了HashMap
  2. LinkedHashMap集合底层是哈希表 + 链表（保证迭代的顺序）
  3. LinkedHashMap集合是一个有序的集合，存储元素和取出元素的顺序是一致的

- Map集合的第一种遍历方式：通过键找值的方式
  Map集合中的方法：  keySet()   返回此映射中包含的键的Set视图
  实现步骤：

  1. 使用Map集合中的keySet()，把Map集合所有的key取出来，存储到一个Set集合中
  2. 通过set集合，获取Map集合中的每一个key
  3. 通过Map集合中的方法get(key)，通过key找到value

- Map集合的第二种遍历方式：使用Entry对象遍历
  Map集合中的方法： entrySet()   返回此映射中包含的映射关系的set图
  实现步骤：

  1. 使用Map集合中的方法entrySet()，把Map集合中多个Entry对象取出来，存储到一个set集合中
  2. 遍历set集合，获取每一个Entry对象
  3. 使用Entry对象中的方法getKey()和getValue()获取键与值

- HashMap存储自定义类型键值

  - Map集合保证key是唯一的：
        作为key的元素，必须重写hashCode方法和equals方法，以保证key唯一

- LinkedHashMap继承了HashMap，是Map接口的哈希表和链接列表的实现，具有可预知的迭代顺序
  底层原理：
      哈希表 + 链表（记录元素顺序）

- Hashtable
  Hashtable底层也是一个哈希表，是一个线程安全的集合，是单线程集合，速度慢，不能存储null值，nukk键
  HashMap地城是一个哈希表，是一个线程不安全的集合，是多线程的集合，速度快，可以存储null值，null键
  Hashtable和Vector集合（HashMap和ArrayList）一样，在jdk1.2版本之后背更先进的集合取代了

  Hashtable的子类Properties依然活跃在历史舞台
  Properties集合是一个唯一和IO流相结合的集合

- JDK9的新特性：
      list接口、set接口、map接口里面增加了一个新的静态的方法of，可以给集合一次性添加多个元素
      `static <E> list<E> of(E...elements)`
      使用前提：当集合中存储的元素的个数已经确定了，不在改变时使用
  注意：

  1. of方法只适用于list接口、set接口、map接口，不适用于接口的实现类
  2. of方法的返回值是一个不能改变的集合，集合不能再使用add、put方法添加元素，会抛出异常
  3. set接口和map接口在调用of方法的时候，不能有重复的元素，否则会抛出异常