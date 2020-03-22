# 关于java的一些记录
## 零散知识点
1. length是数组的长度，length()是字符串的长度，size()是列表中的元素个数
## 关于string
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
## set
### hashset
- `Set <String> strSet = new HashSet(strList)`
- 根据字符串列表创建一个字符串hashset
- `strSet.contains("hello")`
- set类具有方法contains，比如判断里面有没有hello这个字符串