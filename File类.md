### File类

- 相对路径：`java`的相对路径指的是相对于当前目录的根目录

- 获取功能的方法

  - `public String getAbsolutePath()`：返回此File的绝对路径名字符串（不管传入的是绝对路径还是相对路径，返回的都是绝对路径）
  - `public String getPath()`：将此File转换为路径名字字符串（定义的时候传入什么就返回什么）
  - `public String getName()`：返回由此File表示的文件或目录的名称
  - `public long length()`：返回由此File表示的文件的大小，以字节为单位
    注意：
    1. 文件夹是没有大小概念的，不能获取文件夹的大小
    2. 如果构造方法中给出的路径不存在，那么length方法返回0

- 判断功能的方法

  - `public boolean exists()`：将File文件表示的文件或者目录是否实际存在
  - `public boolean isDirectory()`：此File文件是否为目录
  - `public boolean isFile()`：此File表示的是否为文件

- 创建删除功能的方法

  - `public boolean createNewFile()`：当且仅当该名称的文件尚不存在时，创建一个新的空文件
    注意：

    1. 此方法只能创建文件，不能创建文件夹
    2. 创建文件的路径必须存在，否则会抛出异常

  - `public boolean delete()`：删除由此File表示的文件或目录

    1. true：文件/文件夹删除成功，返回true
    2. false：文件夹中有内容，不会删除，返回false；构造方法中路径不存在返回false

    注意：delete方法是直接在硬盘删除文件，不走回收站，删除需谨慎

  - `public boolean mkdir()`：创建由此File表示的目录

  - `public boolean mkdirs()`：创建由此File表示的目录包括任何必需当不存在的父目录

- 目录的遍历

  - `piblic String[] list()`：返回一个String数组，表示该File目录中的所有子文件或目录
  - `public File[] listFiles()`：返回一个File数组，表示该File目录中的所有子文件或目录

  注意：

  1. `list`和`listFiles`方法遍历的是构造方法中给出的目录
  2. 如果构造方法给出的目录的路径不存在，会抛出空指针异常
  3. 如果构造方法中给出的路径不是一个目录，也会抛出空指针异常