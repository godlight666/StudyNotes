# 面向对象特性

## 方法的使用

- public方法：一些类成员变量使用private可以不让外部访问，而使用pubulic方法来修改或读取这个成员，因为方法中可以进行一些限制，防止对成员变量的直接修改，比如将age修改为负数
- private方法：只让同一类中方法调用

## 可变参数

- 可以使用`void setName(String... names)`来定义不定数目的参数，比如可以这样用

    ```Java
    Group g = new Group();
    g.setNames("Xiao Ming", "Xiao Hong", "Xiao Jun"); // 传入3个String
    g.setNames("Xiao Ming", "Xiao Hong"); // 传入2个String
    g.setNames("Xiao Ming"); // 传入1个String
    g.setNames(); // 传入0个String
    ```

## 构造方法

- <font size=5>构造方法没有返回值</font>
- 不写也有默认的，有了默认的就不能用了，可以有多个但是参数不一样，一个构造方法可以用this调用另一个构造方法

## 方法重载

- <font size=5>重载方法的返回值应该相同</font>

## 继承extends

- 除了object，<font color=FF14>其他的类有且仅有一个父类</font>
- private成员不会被继承，protected只会被自己和子类继承
- 子类的构造方法必须调用父类的构造方法，子类不会继承父类的构造方法
- 父类的引用可以指向子类的对象，因为父类有的子类都有，如

   `Person s = new Student("dai",20);`

- 子类的引用不能指向父类的对象，会引发<font color=FF14>ClassCastException</font>，可以用instanceof判断该引用指向的实例是不是这个类或该类的子类：`p instanceof Student`返回的就是false

## 多态性Polymorphic

- 方法重写override和方法重载overload不同，overload是在同一类中，方法参数不同，override是在子类中有一个和父类中方法返回值和参数都完全一样的方法，从而将父类中的该方法覆盖
- <font size=4>如果student中的run方法override了person中的run方法，那么`Person p = new Student();`使用的p.run()应该调用的是student的run方法，即以实例中的方法为准<font color=FF14>,这就是多态性，即针对某个类型的方法调用，运行时才动态的决定实际用的方法。对某个类型调用某个方法，执行的实际方法可能是某个子类的覆写方法</font></font>
- 多态性功能：允许添加更多类型的子类实现功能扩展，不需要基于父类的代码
- 通过super来调用父类中被覆写的方法

## final修饰

- 在保护级别修饰（如public）之后那一个位置
- 修饰类：该类不能被继承
- 修饰方法：该方法不能被override
- 修饰类变量：该变量初始化之后不能被修改，相当于只能赋值一次，并且必须在创建对象时就初始化
- 修饰局部变量：不能被修改

## abstract修饰

- 在保护级别修饰（如public）之后那一个位置
- 修饰类：类里有抽象方法，该类无法实例化，只能实例化子类，由子类实现抽象方法
- 修饰方法：必须在抽象类里，子类必须override该方法

    ```Java
    abstract class Person {
        public abstract void run();
    }
    ```

## interface接口

- 接口是比抽象类还抽象的。接口中不允许有变量（只能有静态变量，且被public static final修饰），所有的方法都是public abstract

   ```java
   interface Person {
    void run();
    String getName();
    }
   ```

- 一个类实现接口用`implements`，一个类可以实现多个接口`class Strudent implements Person,Hello{}`，一个类实现该接口必须是写接口中所有的抽象方法。
- 一个接口也可以继承另一个接口

### default方法

- 在接口中定义的default方法，实现该接口的类中不一定要override该方法，这样在接口中新增方法后，只需要修改制定的实现类就可以了，不需要修改所有的实现类

## 关于interface和abstract class

### 为什么要有interface

因为java中为了避免多重继承可能带来的继承关系混乱所以只允许单一继承，java为了 满足多重继承的需要，采用了规格的多重继承即接口,如果使用，即使没有继承关系的不同种类的对象也可以做共通的处理（我们可以在接口中定义一个方法，然后在两个没有继承关系的对象的不同父类中写一个相同方法签名和返回类型的方法）

### 接口和抽象类的区别

1. 接口的方法默认是 public，所有方法在接口中不能有实现(Java 8 开始接口方法可以有默认实现），而抽象类可以有非抽象的方法。
2. 接口中除了static、final变量，不能有其他变量，而抽象类中则不一定。
3. 一个类可以实现多个接口，但只能实现一个抽象类。接口自己本身可以通过extends关键字扩展多个接口。
4. 接口方法默认修饰符是public，抽象方法可以有public、protected和default这些修饰符（抽象方法就是为了被重写所以不能使用private关键字修饰！）。
5. 从设计层面来说，抽象是对类的抽象，是一种模板设计，而接口是对行为的抽象，是一种行为的规范。

### 类实现两个接口有同名方法时会发生的几种情况

1. 两个接口方法签名相同返回类型相同时 不会编译出错，可以直接override
2. 两个接口方法签名相同返回类型不同，会编译出错。
3. 两个接口方法名相同,在实现类里这两个同名方法签名符合overload条件的话可以同时实现不会报错，只要符合overload那方法返回类型就不重要了，一样不会报错。

### 类实现两个接口有同名default方法时会发生的几种情况

1. 如果两个方法的方法签名相同方法返回类型相同那么需要在实现类override这个同名方法。
2. 如果两个方法方法签名相同，返回类型不同会编译出错。
3. 如果两个方法符合overload条件可以正常实现

### 关于接口中的静态方法，静态变量

- 静态变量：可以通过实现类和实现类的实例访问到
- <font size=4>静态方法：无法通过实现类和它的实例访问到</font>

## static

- 静态变量：属于类的变量，所有该类的实例共享该变量<font color=FF14>推荐用类名访问</font>,如 Person.num
- 静态方法：属于class，直接用类名调用,<font color=FF14>方法内部只能访问class的静态变量，不能用this</font>
- 在接口中，只能有public static final 修饰的变量

## package包

### import包名逻辑

import的包名：开头为当前文件夹的父文件夹下那个类所在的文件的文件夹，即在src/pack1/test1.java中要引入src/pack2/test2.java中的类，只需要`import pack2.test2`。或者目标文件在当前文件所在文件夹的子文件夹中，比如src/test3.java也要用test2中的，就直接`import pack2.test2`

- 父包与子包：如org.it.315.* 和 org.it315.example.*。父包中的类调用子包中的类，必须用子包的全名，不能省略父包名部分
- 父包是父包，子包是子包，导入父包不会导入子包

### JVM寻找类

- 先查找当前package是否存在该class
- 查找import的包是否包含该class
- 查找Java.lang包是否包含该class

## 作用域

### public

- class/interface：可以被其他任何类访问
- 变量/方法：<font size=4>只要能访问该类</font>，就能访问
- <font color=FF14>一个.java只能有一个public类</font>

### private

- 不能修饰类
- 修饰类成员：无法被其他类访问（class内部的类可以访问，即嵌套类）

### protected

- 不能修饰类
- 主要用于继承，可以被子类访问，也可以被同一包中其他类访问

### default

- 类：可以被同一包中的类访问
- 类成员：可以被同一包中的类访问

## classpath

- 运行时可以通过-cp制定，用来告诉JVM去哪里搜索程序中的class，不同的路径用“；”分割，Linux中用“：”分割。默认从当前文件夹中搜

## jar

- 相当于目录，包含很多.class，方便下载和使用，子文件夹直接就是各个包。即hello.jar/ming/Person.class,而不应该是hello.jar/bin/ming/Person.class
- jar相当于.class的容器
- 要创建jar，直接将几个包打包压缩成zip格式，然后修改为.jar后缀就可。<font size=5>注意！是把几个class所在文件夹打包，即编译后的，不是java文件</font>
- MANIFEST.MF文件可以提供jar包的信息，如Main-Class，这样可以直接运行jar包，因为告诉了入口`java -jar hello.jar`

## 模块module

- 将jar进一步封装，还可以跟jre一起打包，只用jre的部分模块