# 关于java的一些记录

## 零散知识点
1. length是数组的长度，length()是字符串的长度，size()是列表中的元素个数
2. 对于一个String类型的变量str，不能直接str[0]来获取字符串的第一个字符，要用charAt()
## 关于string
### [String底层实现](https://www.cnblogs.com/xiaoxi/p/6036701.html)
- `String str = new String("abc");`中有两个对象，字符串常量池中一个（编译时创建），堆中一个（运行时创建），还创建了一个引用（在栈中）
### string，stringBuilder，stringBuffer
- String是一个类，即一个引用类型，而不是基础数据类型
- String：是一个常量，创建之后不可变。str+"abc"本质上是创建了一个新的String，而不是改变原本的String，速度最慢
- `String str = "example string"`
- StringBuilder：是一个变量，线程不安全，速度快
- `StringBuilder strb = new StringBuilder("example string")`
- StringBuffer：是一个变量，线程安全，速度中等
- 后面两个需要使用toString()变为String类型
### subString子串
- 这三个类都有public String subString（int begin,int end)方法获取指定位置的子串
### indexO寻找子串
- `int indexof(String str)`返回第一次找到该子串的位置
### charAt 获得字符
- `str.charAt(num)`来获取num位置的字符
## 关于数组Arrays
- Arrays.sort(arr)使用快速排序对数组arr进行排序
- Arrays.toString(arr)将数组变为字符串
## 关于面向对象
### 方法的使用
- public方法：一些类成员变量使用private可以不让外部访问，而使用pubulic方法来修改或读取这个成员，因为方法中可以进行一些限制，防止对成员变量的直接修改，比如将age修改为负数
- private方法：只让同一类中方法调用
### 可变参数
- 可以使用`void setName(String... names)`来定义不定数目的参数，比如可以这样用
```
Group g = new Group();
g.setNames("Xiao Ming", "Xiao Hong", "Xiao Jun"); // 传入3个String
g.setNames("Xiao Ming", "Xiao Hong"); // 传入2个String
g.setNames("Xiao Ming"); // 传入1个String
g.setNames(); // 传入0个String
```
### 构造方法
- <font size=5>构造方法没有返回值</font>
- 不写也有默认的，有了默认的就不能用了，可以有多个但是参数不一样，一个构造方法可以用this调用另一个构造方法
### 方法重载
- <font size=5>重载方法的返回值应该相同</font>
## set
### hashset
- `Set <String> strSet = new HashSet(strList)`
- 根据字符串列表创建一个字符串hashset
- `strSet.contains("hello")`
- set类具有方法contains，比如判断里面有没有hello这个字符串