# JAVA基础面试题30道

## 1.JDK和JRE有什么区别?

```xml
JDK（Java Development Kit） java开发工具包，包含JRE和java的基础类库和一堆java工具（javac/java/jdb）

JRE（Java Runtime Environment） Java运行环境,包含JVM和java核心类库lib

JVM（Java Virtual Machine）java虚拟机

三者联系：JVM不能单独搞定class的执行，解释class的时候JVM需要调用解释所需要的类库lib。在JDK下面的的jre目录里面有两个文件夹bin和lib,在这里可以认为bin里的就是jvm，lib中则是jvm工作所需要的类库，而jvm和 lib和起来就称为jre。JVM+Lib=JRE。总体来说就是，我们利用JDK（调用JAVA API）开发了属于我们自己的JAVA程序后，通过JDK中的编译程序（javac）将我们的文本java文件编译成JAVA字节码，在JRE上运行这些JAVA字节码，JVM解析这些字节码，映射到CPU指令集或OS的系统调用。
```

## 2.开发Java程序的步骤

![在这里插入图片描述](https://img-blog.csdnimg.cn/20191220114753647.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3dlaXhpbl80NDA2NDE1Nw==,size_16,color_FFFFFF,t_70)

```
编译：
    是指将我们编写的Java源文件翻译成JVM认识的class文件，在这个过程		中， javac 编译器会检查我们所写的程序是否有错误，有错误就会提示出	来，如果没有错误就会编译成功。

运行：
    是指将 class文件 交给JVM去运行，此时JVM就会去执行我们编写的程序		了。

```

## 3.变量是什么?变量的三要素是什么?

```
变量：变量是存储信息（数据）的容器。
语法： [ 修饰符 ] 数据类型 变量名字 [赋值操作]

变量的三要素：
1.数据类型 ： 决定在内存中分配的空间
2.变量名 ： 空间别名
3.值 ：空间中存储的数据
```

## 4.变量的命名规范

```

1.变量有数字,字母和_组成.

2.变量不能以数字开头.

3.变量区分大小写.

4.变量不要过长,且命名要有意义.

5.变量命名尽量使用驼峰或_进行命名.

```

## 5.java数据类型和默认值

![image-20200827193125904](C:\Users\chd19\AppData\Roaming\Typora\typora-user-images\image-20200827193125904.png)

## 6.基本数据类型转换的规则

```
1、boolean不能参与类型转换,其它都行。
2、没有超出byte short char的范围,整数可以直接赋值。
3、自动类型转换 小——>大
	byte < short(char) < int < long < float < double
4、强制类型转换 大 ——>小 需要加上强制类型转换符
5、byte short char混合运算,先各自转换成int,再做运算。
6、多种数据类型混合运算的时候,各自先转换成容量最大的哪一种再做运算。
```

## 7.==与.equals()有什么不同

```java
1.两者的区别:
== 为运算符
equal 为String数据类型的比较方法.equal()

2.两者的比较范围:
一方面是基础数据类型（例如 int a = 1），== 与 equal 都是作用于比较对象内容（堆）是否相同。
另一方面则是引用对象类型（例如 int a = new  int(1)）， == 与 equal 都是作用于比较对象内存地址（栈）是否相同。

3.需要注意的是
 1.equal在源码中的实现为一下存在形式，可以被重写

public boolean equals(Object obj) {
 return (this == obj);
}

 2.相同内容的对象地址不一定相同，但相相同地址的对象内容一定相同。
```

## 8.单|&与双|&& (短路)区别?

```
单个的逻辑运算符会将左右两个表达式都进行运算得出布尔值，再进行运算。‘短路与’若左边表达式为false则不会对右边的表达式进行判断，

　　　　因为结果必为false；‘短路或’若左边表达式结果为true则不会对右边的表达式进行判断，因为结果必为true。

　　　　　　短语的逻辑运算符相当于普通的逻辑运算符效率更高些。
```

## 9.if... else和写两个if区别

```
多个if   不管你前面ture与否后面的都执行  
else  if    如果前面的有一个成立  那么后面的都不执行 
```

## 10.switch( )接受的数据类型

```
在JDK1.5之前,switch循环只支持byte short char int四种数据类型.

JDK1.5 在switch循环中增加了枚举类与byte short char int的包装类,对四个包装类的支持是因为java编译器在底层手动进行拆箱,而对枚举类的支持是因为枚举类有一个ordinal方法,该方法实际上是一个int类型的数值.

jdk1.7开始支持String类型,但实际上String类型有一个hashCode算法,结果也是int类型.而byte short char类型可以在不损失精度的情况下向上转型成int类型.所以总的来说,可以认为switch中只支持int.
```

## 11.break、 continue和return的 区别?

```
一、作用不同

1、break：执bai行break操作，跳出所在的du当前整个循环，到外层代码继续执行。

2、continue：执行continue操作，跳出本次循环，从下一个迭代继续运行循环，内层循环执行完毕，外层代码继续运行。

3、return：执行return操作，直接返回函数，所有该函数体内的代码（包括循环体）都不会再执行。

二、结束不同

1、break：break不仅可以结束其所在的循环，还可结束其外层循环，但一次只能结束一种循环。

2、continue：continue结束的是本次循环，将接着开始下一次循环。

3、return：return同时结束其所在的循环和其外层循环。
三、紧跟不同

1、break：需要在break后紧跟一个标签，这个标签用于标识哪个外层循环。

2、continue：在continue后不需要加参数。

3、return：在return后需要紧跟一个返回值，用于提供给对应方法所需的返回值。
```

## 12.什么是数组，它有什么特征?

```
数组，是有序的元素序列，用于储存多个相同类型数据的集合，数组是在程序设计中，为了处理方便， 把具有相同类型的若干元素按无序的形式组织起来的一种形式。这些无序排列的同类数据元素的集合称为数组
```

## 13.数组的创建 与使用方式

```
1.int java[]= new int[]{1,2,3,4.5.6};//第一种
2.//第二种：
3.int java[]={1,2,3,4,5,6};
4.//第三种：
5.int java[]=new int[6];</span>
```

## 14.方法的定义和使用

```
方法的声明：
1、方法是完成某个功能的一组语句，通常将某个功能写成一个方法
2、定义方法就是编写有特定功能的一段代码，在程序中使用同样功能的地方可以调用定义好的方法，实现代码的重用
方法声明或称为定义方法：
无返回值方法的调用
有返回值方法的调用
同一个类方法调用
不同类方法调用
```

## 15.Arrays.工具类常用方法?

```java
1、声明数组
    1.String[] aArray = new String[5];  
    2.String[] bArray = {"a","b","c", "d", "e"};  
    3.String[] cArray = new String[]{"a","b","c","d","e"};  

2、打印数组
    1.int[] intArray = { 1, 2, 3, 4, 5 };  
    2.String intArrayString = Arrays.toString(intArray);  
    3.   
    4.// 直接打印,则会打印出引用对象的Hash值  
    5.// [I@7150bd4d  
    6.System.out.println(intArray);  
    7.  
    8.// [1, 2, 3, 4, 5]  
    9.System.out.println(intArrayString);  

3、根据数组创建ArrayList
    1.	String[] stringArray = { "a", "b", "c", "d", "e" };  
    2.ArrayList<String> arrayList = new ArrayList<String>(Arrays.asList(stringArray));  
    3.// [a, b, c, d, e]  
    4.System.out.println(arrayList);  

3. 检查数组是否包含某个值
    1.String[] stringArray = { "a", "b", "c", "d", "e" };  
    2.boolean b = Arrays.asList(stringArray).contains("a");  
    3.// true  
    4.System.out.println(b);  
4. 合并连接两个数组
      int[] intArray = { 1, 2, 3, 4, 5 };  
      int[] intArray2 = { 6, 7, 8, 9, 10 };  
      // Apache Commons Lang 库  
      int[] combinedIntArray = ArrayUtils.addAll(intArray, intArray2); 
5. 声明内联数组
	1.method(new String[]{"a", "b", "c", "d", "e"});  
6. 用给定的字符串连结(join)数组
    1.// containing the provided list of elements  
    2.// Apache common lang  
    3.String j = StringUtils.join(new String[] { "a", "b", "c" }, ", ");  
    4.// a, b, c  
    5.System.out.println(j);  
7. 将ArrayList转换为数组
    1.String[] stringArray = { "a", "b", "c", "d", "e" };  
    2.ArrayList<String> arrayList = new ArrayList<String>(Arrays.asList(stringArray));  
    3.String[] stringArr = new String[arrayList.size()];  
    4.arrayList.toArray(stringArr);  
    5.for (String s : stringArr)  
    6.    System.out.println(s);  
8. 将数组转换为Set
    1.Set<String> set = new HashSet<String>(Arrays.asList(stringArray));  
    2.//[d, e, b, c, a]  
    3.System.out.println(set);  
9. 数组元素反转
    1.int[] intArray = { 1, 2, 3, 4, 5 };  
    2.ArrayUtils.reverse(intArray);  
    3.//[5, 4, 3, 2, 1]  
    4.System.out.println(Arrays.toString(intArray));  
10. 移除元素
      byte[] bytes = ByteBuffer.allocate(4).putInt(8).array();  
         
      for (byte t : bytes) {  
         System.out.format("0”)
```

## 16.什么是面向对象?

```
面向对象的方法主要是把事物给对象化，包括其属性和行为。面向对象编程更贴近实际生活的思想。总体来说面向对象的底层还是面向过程，面向过程抽象成类，然后封装，方便使用就是面向对象
```

## 17.什么是对象?什么是类?类与对象的关系?

```
类的概念 ： 类是具有bai相同属du性和服务的一组对象的集合。为属于该类zhi的所有对象提供了dao统一的抽象描述，其内部包括属性和服务两个主要部分。在面向对象的编程语言中，类是一个独立的程序单位，应该有一个类名并包括属性说明和服务说明两个主要部分。
对象的概念：对象是系统中用来描述客观事物的一个实体，是构成系统的一个基本单位。一个对象由一组属性和对这组属性进行操作的一组服务组成。从更抽象的角度来说，对象是问题域或实现域中某些事物的一个抽象，它反映该事物在系统中需要保存的信息和发挥的作用；它是一组属性和有权对这些属性进行操作的一组服务的封装体。客观世界是由对象和对象之间的联系组成的。
类与对象的关系就如模具和铸件的关系，类的实例化结果就是对象，而对一类对象的抽象就是类。类描述了一组有相同特性( 属性 ) 和相同行为 ( 方法 ) 的对象。
```

## 18.如何定义一个类

```
类是用class关键字来定义的一种抽象数据类型，类不但定义了抽象数据类型的组成（成员变量），同时还定义了对该类型可以实施的操作（方法），类名的首字母必须大写
```

## 19.什么是构造方法

```
构造方法是一种特殊的方法，与一般的方法不同是：
1.构造方法的名字必须与定义他的类名完全相同，没有返回类型，甚至连void也没有。
2.构造方法的调用是在创建一个对象时使用new操作进行的。构造方法的作用是初始化对象。
3.不能被static、final、synchronized、abstract和native修饰。构造方法不能被子类继承。
```

## 20.什么是封装?

```
封装即隐藏对象的属性和实现细节，仅对外公开接口，控制在程序中属性的读和修改的访问级别；将抽象得到的数据和行为（或功能）相结合，形成一个有机的整体，也就是将数据与操作数据的源代码进行有机的结合，形成“类”，其中数据和函数都是类的成员。”
```

## 21.JAVA中访问修饰符有哪些?

 

```
· public

  被 public 修饰的成员变量和方法可以在任何类中都能被访问到。
  被 public 修饰的类，在一个 java 源文件中只能有一个类被声明为 public ，而且一旦有一个类为 public ，那这个 java 源文件的文件名就必须要和这个被 public 所修饰的类的类名相同，否则编译不能通过。

· protected

  被 protected 修饰的成员会被位于同一 package 中的所有类访问到，也能被该类的所有子类继承下来。

· friendly

  默认，缺省的。在成员的前面不写访问修饰符的时候，默认就是友好的。
  同一package中的所有类都能访问。
  被 friendly 所修饰的成员只能被该类所在同一个 package 中的子类所继承下来。
  

· private

  私有的。只能在当前类中被访问到
```

## 22.this、super的用法与区别?

```
this()代表调用同一个类中的其它构造器
super()用于调用父类中的构造方法

super()和this()均需放在构造方法内第一行

this()和super()都指的是对象，所以，均不可以在static环境中使用。包括：static变量,static方法，static语句块。

this和super不能同时出现在一个构造函数里面

this()和super()为构造方法，作用是在JVM堆中构建出一个对象。

因此避免多次创建对象，同一个方法内只能调用一次this()或super()。

同时为了避免操作对象时对象还未构建成功，需要this()和super()的调用在第一行实现【以此来创建对象】，防止异常。
```

## 23.重写与重载的区别

```
方法的重载和重写都是实现多态的方式，区别在于前者实现的是编译时的多态性，而后者实现的是运行时的多态性。重载发生在一个类中，同名的方法如果有不同的参数列表（参数类型不同、参数个数不同或者二者都不同）则视为重载；重写发生在子类与父类之间，重写要求子类被重写方法与父类被重写方法有相同的参数列表，有兼容的返回类型，比父类被重写方法更好访问，不能比父类被重写方法声明更多的异常（里氏代换原则）。重载对返回类型没有特殊的要求，不能根据返回类型进行区分。
```

## 24.抽象类必须要有抽象方法吗，和普通类有哪些区别?

```
普通类不能包含抽象方法，抽象类可以包含抽象方法。

抽象类不能直接实例化，普通类可以直接实例化
```

## 25.抽象类能使用final修饰吗?

```
不能，定义抽象类就是让其他类继承的，如果定义为 final 该类就不能被继承，这样彼此就会产生矛盾，所以 final 不能修饰抽象类，编辑器也会提示错误信息
```

## 26.接口和抽象类有什么区别?

![img](file:///C:\Users\chd19\AppData\Local\Temp\ksohtml17468\wps1.jpg) 

## 27.Java容器都有哪些?

```
 Array，String（底层是char[]），collection（包含List,Set），Queue，Map
```

## 28.List、 Set、 Map之间的区别

```
\1. List 集合中对象按照索引位置排序，可以有重复对象，允许按照对象在集合中的索引位置检索对象，例如通过list.get(i)方法来获取集合中的元素；

 \2. Map 中的每一个元素包含一个键和一个值，成对出现，键对象不可以重复，值对象可以重复；

 \3. Set 集合中的对象不按照特定的方式排序，并且没有重复对象，但它的实现类能对集合中的对象按照特定的方式排序，例如 Tree Set 类，可以按照默认顺序，也可以通过实现 Java.util.Comparator< Type >接口来自定义排序方式。
```

## 29.hashmap的实现原理

```
首先有一个每个元素都是链表（可能表述不准确）的数组，当添加一个元素（key-value）时，就首先计算元素key的hash值，以此确定插入数组中的位置，但是可能存在同一hash值的元素已经被放在数组同一位置了，这时就添加到同一hash值的元素的后面，他们在数组的同一位置，但是形成了链表，同一各链表上的Hash值是相同的，所以说数组存放的是链表。而当链表长度太长时，链表就转换为红黑树，这样大大提高了查找的效率。 
```

## 30.ArrayList和linkedlist的区别

```
\1. ArrayList是实现了基于动态数组的数据结构，LinkedList是基于链表结构。

\2. 对于随机访问的get和set方法，ArrayList要优于LinkedList，因为LinkedList要移动指针。

\3. 对于新增和删除操作add和remove，LinkedList比较占优势，因为ArrayList要移动数据。
```

