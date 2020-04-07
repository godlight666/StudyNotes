# String 及相关类

## [String底层实现](https://www.cnblogs.com/xiaoxi/p/6036701.html)

- `String str = new String("abc");`中有两个对象，字符串常量池中一个（编译时创建），堆中一个（运行时创建），还创建了一个引用（在栈中）

## string，stringBuilder，stringBuffer

- String是一个类，即一个引用类型，而不是基础数据类型
- String：是一个常量，创建之后不可变。str+"abc"本质上是创建了一个新的String，而不是改变原本的String，速度最慢
- `String str = "example string"`
- StringBuilder：是一个变量，线程不安全，速度快
- `StringBuilder strb = new StringBuilder("example string")`
- StringBuffer：是一个变量，线程安全，速度中等
- 后面两个需要使用toString()变为String类型

## String中的方法

## subString子串

- 这三个类都有public String subString（int begin,int end)方法获取指定位置的子串

## indexof寻找子串

- `int indexof(String str)`返回第一次找到该子串的位置

## charAt 获得字符

- `str.charAt(num)`来获取num位置的字符
