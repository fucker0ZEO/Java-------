Arraylist  查询操作比较多时用它，如果既有查询又有增删时也用它。平时增删操作较少，查询居多

Lnkedlist 增删操作比较多时用它 

set中主要是看子类对象，方法和coliection一样

Hashset底层结构为哈希表,HashMap的简化版

## Hashset的一致性，无序性，哈希表结构

哈希表存放时是按照哈希值大小存的，不是按照存入顺序

哈希值如果一样呢？

还有一次校验方式！equals方法判断元素对象是否相同

它会在同一个位置顺延。

取出只有迭代器这一种方式

而且保证 唯一性

数组本身也是容器，效率最高，缺陷是不够灵活

不能扩容

Java中容器就是集合，翻译问题

array list用数组实现

Linkedlist用链表实现

map用键值对来实现

## 泛型

### 自定义泛型



容器后进先出，泛型类似于标签对容器分类，建立类型安全的容器

 泛型是JDK1.5以后增加的，它可以帮助我们建立类型安全的集合。在使用了泛型的集合中，遍历时不必进行强制类型转换。JDK提供了支持泛型的编译器，将运行时的类型检查提前到了编译时执行，提高了代码可读性和安全性。

   泛型的本质就是【“数据类型的参数化”】。 我们可以把“泛型”理解为数据类型的一个【占位符(形式参数)】，即告诉【编译器】，在【调用泛型时必须传入实际类型】。<u></u>



get()可以获取对应位置索引的内容！

Intege 整型

学源码，并不是要所有的内容都读通！一个类就有好几千行代码

可能会以月为单位的花费时间！！！

学源码的目的是为了更好的理解概念！而不是为了读通！！！

collection和List，Set都是接口。collection分出2个子接口

### 测试collection接口的方法

定义泛型后面就只能放泛型对应的数据类型了

size() 获取该集合的长度

isEmpty（）判断该集合是否为空，是则返回true，非空为false

add()添加元素，如果 定义了泛型就只能添加对应的元素

remove()移除，并不是删除，实质上是拷贝+移位覆盖，对象删除了引用地址离开了容器，但是还在内存中

容器中存的是地址

clear()移除所有的元素，循环用null覆盖

toArray()转化出一个Object[]数组来

contains()根据equals()来判断是否包含

#### 以下为操作2个容器

取合

addAll(x),将x中的元素拷贝一份到另一个集合中去 



去交集，或者去重

removeAll(x),去除该集合中和x集合重复的部分，被操作的只有该集合，x集合不变，使用的是移位覆盖！

取交集

retainAll(x),用该集合和x集合重复的部分，覆盖该集合，被操作的同样只有该集合，x集合不变。

List有序，可重复的容器。2个是数组(ArrayList和Vector)，一个是链表(LinkedList)

Set无序，不可重复的容器。结构是哈希表。所谓的无序是从取出时的打印结果来看的，放入和取出时顺序不一样！实际存储时不是按照放入顺序存储的，它是按照Hash值取余存储的。而相对于哈希表内部来说，还是有序的。HashSet是HashMap的简化版。ThreeSet是红黑树。

####List中常见的三个实现类 

ArrayList,LinkList和Vector 第一个 用的最多，底层数据结构是数组，线程不安全

LinkList用的是链表

Vector用的也是数组，只不过 是线程安全的数组，效率低，有同步锁，用的是关键字锁。

ArrayList中的方法

这里是ArrayList中的方法，和collection中的方法有点区别（区别在角标，或者说是索引上面，因此说ArrayList便于查询）

add可以通过角标插入 （a,x） a表示角标数，x表示要插入 的数据，或者说是被操作的数据

set()可以通过角标修改。list01.set(1,"java"); 和System.out.println("list01"+list01);

结果为list01[aa,java,bb] 角标为1的bb就被java这个元素替换了

get()可以通过角标获取，获取该角标所对应元素。

这些都是和顺序相关，也就是和索引相关的方法

indexOf（）返回第一次出现的指定元素的索引位置，即角标数。若无则返回-1

lastIndexOf（）返回最后一次出现的指定元素的索引位置，即角标数.若无则返回-1。可以相当于从右往回找。终究还是返回的是角标数，无论是正向索引还是反向索引，同一个元素的角标都是一样的！元素放入容器中时，角标就已经确定了！

  我们知道，数组长度是有限的，而ArrayList是可以存放任意数量的对象，长度不受限制，那么它是怎么实现的呢?【本质上就是通过定义新的更大的数组，将旧数组中的内容拷贝到新数组，来实现扩容。目前是原长度除2变为更大的数组】 ArrayList的Object数组初始化长度为10，如果我们存储满了这个数组，需要存储第11个对象，就会定义新的长度更大的数组，即长度为15，并将原数组内容和新的元素一起加入到新数组中，源码如下： 

添加一个新元素时 先检测size+1 这个长度是否够。然后size++ 长度增加，返回true

如果是长度不够则

int newCapacity = oldCapacity + (oldCapacity>>1)

老数组右移1位然后加上原来的老数组，再赋值给新的数组

右移效率更高

remove看上去是删除，实际上也是拷贝

删除某元素，实际上是需要移动后面的所有元素来覆盖到该元素的位置，也就是说实际该角标后的上所有元素都向前移动1位来覆盖。例：a,b,c,d四个元素，现在要在角标1处删除一个元素，然后从角标1后面的元素都覆盖到之前上。也就是说c覆盖了b,d覆盖了c。

插入也是类似的（只有 在ArrayList中才有按照角标插入），本质上也是拷贝。将该元素放到默认的角标位置后，需要将该角标以及其后的所有元素都拷贝一遍，覆盖到之前的元素上。例：a,b,c,d四个元素，现在要在角标1处插入一个元素f，将f覆盖到角标1上，然后从角标1开始，以及后面的元素都覆盖到之前上。也就是说b覆盖了c,c覆盖了d。也相当于后移一位的整体覆盖。

因此增删效率低！

clear则是写了一个循环依次清空。null覆盖清空。

public void clear()

{

​	modCount++;

​	for(int i =0 ; i<size;i++)

​		//通过null将角标处的元素覆盖即为清空

​		elementDate[i] = null;

​      size =0



}

#### 自定义实现一个ArrayList



default

![b442](C:\Users\fucker\Pictures\b442.PNG)
![](C:\Users\fucker\Pictures\b441.PNG)

什么时候扩容？？

if(size == elementData.lenght)

//怎么扩容??

Object[] newArray = new obejct[elementDate.length+(elementDate.length>>1)];

//这里需要（）,乘除的优先级高于加，不然就是(10+10)/2 结果还是10 



//通过（）才能够10-->10+10/2        （）解决移位算法优先级问题

//系统提供的拷问方法

System.arraycopy(elementDate.0,newArray,0,elementDate);

elementDate = new Array;

## 写代码时，调试要注意！写一个功能模块 之后就可以开始调试了，后面的优化慢慢加！可以加断点来调试



Vector有同步（关键字）锁（但不是每个都有） 线程安全，但是效率低。多线程共享时可以使用这个。

#### Map接口

Map就是用来存储“键(key)-值(value) 对”的。 Map类中存储的“键值对”通过键来标识，所以“键对象”不能重复。

   Map 接口的实现类有HashMap、TreeMap、HashTable、Properties等

Map需要定义泛型 k，v都要分别定义

键和值关联起来成对存放！

值是一个对象（数据结构中的对象）！

//这里选择的键是Integer类型，值是String类型

Map<Integer,String> m1 = new HasMap<>();







常见的Map方法

//通过put()存放键值对

m1.put(1,"one");

m1.put(2,"two");

//get(x),这个方法，通过x这个键，查找得到值的对象

sop(m1.get(1));

结果是取到了one，通过1这个键，取到了one这个值对！

//删除键对象对应的值

remove() 

//包含键值对的数量

int size()

//Map是否为空

isEmpty()

//清空map对象所有键值对

clear()

## 请准确区分出，对单一对象操作的方法和面向整个集合操作的方法！！！



//集合中是否包含x这个键

containskey(x)

//是否包含y这个值

containsValue(y)

//将m2整体添加到m1中

m1.putAll(m2);

**键不能重复！如果重复，则新的覆盖旧的。是否重复也是根据equals()方法**

### Map的另外一些常用方法



## HashMap底层!!!

由哈希表实现。基本结构是数组+链表

结合了两者的优点，增删改查都6

每一个hash key Value next 这四个部分构成了结点对象！

每一个节点对象都是hash值，key对象，Value对象，next这4个部分！

![](C:\Users\fucker\Pictures\b443.PNG)


**牢记此图**

数组长度为16

![](C:\Users\fucker\Pictures\b444.PNG)

通过一个算法key.Value()%16取余，余数为0~15

按照对应的余数放到对应的地方

![](C:\Users\fucker\Pictures\b446.PNG)

当余数为15时，该节点对象存放在15哪里，并且其中next处为空。余数又为15时，值就在后面顺延一份位置，4个对应的小格子，之前的15的next处被填满！同时该值指向新进来的节点对象，而新值的next也为空。如果此时又来一个节点对象，余数为6，然后改节点对象存放在6的位置，并且next处为空



一种极端最差的散性算法：hascode()/hascode()  这样除出来的结果就是单一的了，所有哈希值都在一个位置后面顺延，其他位置都没有用了，这样的哈希表就退化成了一个链表！

另外一种比较极端的算法可以直接退化成一个数组，会大量消耗资源空间。

因此需要折衷来充分利用空间

 ii. 一种简单和常用的算法是(相除取余算法)：

​      hash值 = hashcode%数组长度

​      这种算法可以让hash值均匀的分布在[0,数组长度-1]的区间。 早期的HashTable就是采用这种算法。但是，这种算法由于使用了“除法”，效率低下。JDK后来改进了算法。首先约定数组长度必须为2的整数幂，这样采用位运算即可实现取余的效果：hash值 = hashcode&(数组长度-1)。

总之是想通过好的hash算法让它又散列又均匀，以提供查询效率

 JDK8中，当链表长度大于8时（即一个位置时有8个节点对象），链表就转换为红黑树，这样又大大提高了查找的效率。 

**hash码和hash值是两个东西，hash值是hash码被除后产生的余数, hashcode是一个整数 ,转化为2进制就是hash码**

 当添加一个元素(key-value)时，首先计算key的hash值，以此确定插入数组中的位置，但是可能存在同一hash值的元素已经被放在数组同一位置了，这时就添加到同一hash值的元素的后面，他们在数组的同一位置，就形成了链表，同一个链表上的Hash值是相同的，所以说数组存放的是链表。 JDK8中，当链表长度大于8时，链表就转换为红黑树，这样又大大提高了查找的效率。 

#### 取数据过程

 (1) 获得key的hashcode，通过hash()散列算法得到hash值，进而定位到数组的位置。

   (2) 在链表上挨个比较key对象。 调用equals()方法，将key对象和链表上所有节点的key对象进行比较，直到碰到返回true的节点对象为止。

   (3) 返回equals()为true的节点对象的value对象。

get(key)  取数据，也是先得到最后hash值，然后依次去找到相应的链表。但是链表中可能有多个hash值，这时就需要用equals()方法，挨个比较其中的key对象,如果是true就认为是找到了，然后将Value对象返回去！！

 因此 Java中规定，两个内容相同(equals()为true)的对象必须具有相等的hashCode。因为如果equals()为true而两个对象的hashcode不同;那在整个存储过程中就发生了悖论。 

hashcode()相当于身份证

扩容问题，类似于之前的扩容！！！

手动实现一个hashMap

![](C:\Users\fucker\Pictures\b447.PNG)

自定义类进行排序

需要实现compare接口

负数对应小于，0对应等于，正数对应大于

```
if(this.salary>0.salary){

return  1;

}else if(this.salary<0.salary){

return -1;

}else{

​      if(this.id>0.id){

return 1;

}else if(this.id<0.id){

return -1;

}else{

return 0;

}

}


```

HashMap:线程不安全，效率高。允许key或value为null.

HashTable:线程安全，效率低。不允许key或value为null.（要做非空这样的重复检查？？？）

HashMap和HashTable则是方法相同，用法很像

**Set接口**

特点无序,和collection方法一样,但是有重要的子类，HashSet和ThreeSet。

```java
//建了一个HashSet对象set1，它实现了Set接口
Set<Strinng> set1 = new HashSet<>();

set1.add("aa");
set1.add("bb");
set1.add("aa");
System.out.println(set1);
//打印结果为 [aa,bb] 少了一个aa，，表示Set不可重复
set1.remove("bb");
//remove移除集合中的“bb”这个元素
System。out.println(set1);
//打印结果为[aa]，表示bb已经被移除了

再建立了一个HashSet对象set2，它实现了Set接口
Set<Strinng> set2 = new HashSet<>();
set1.add("java");
//addAll(x)将x集合中的元素拷贝到另一个集合中
//这里结果[aa,java]
set2.addAll(set1);











```

 HashSet是采用哈希算法实现，底层实际是用HashMap实现的(HashSet本质就是一个简化版的HashMap) 

set中的所有元素都在Map中做key。Value是new Object()

因为是Map实现的，使用的是hash算法，因此是不能是真正重复的（键值对的原因）

TreeSet底层是TreeMap，内部是一个简化的TreeMap（而TreeMap底层是红黑树），也是通过key来存储Set的元素。TreeSet内部需要对存储的元素进行排序，因此，我们对应的类需要**实现Comparable接口**。

**这样，才能根据compareTo()方法比较对象之间的大小，才能进行内部排序！**





| id                 姓名                 年龄                薪水          入职日期 |
| :----------------------------------------------------------- |
| 1001               张三                  27                   20000           2018.5.5 |
| 1002               李四                   30                   30000          2005.4.4 |
| 1003                王五                   18                   3000            2020.5.4 |
|                                                              |

每一行数据使用一个：Map。

整个表格使用一个：List。

ORM思想：对象关系映射

不一定是 List可能是任意容器



为了处理乱码，出现了字符流。它可以指定使用的编码表是UTF-8还是jbk.

乱码的出现是因为两张编码表中的字符对应的位置不同，表用错就可能产生“错位”，进而造成乱码。

通用字节流！字符流基于字节流

字节流2个抽象基类：

一个读（InputStream），一个写(OutputStream)

字符流2给抽象基类：

一个读者(Reader)，一个作者(Writer)

四类派生的子类都是以其父类作为子类的后缀名，前缀名是功能。

IO流，读和写

#### 字符流的特点

主要 方法是“写”

既然IO流是用于操作数据的，那么数据的最常见体现形式是：文件

需求：硬盘上建一个文件，写入一些数据

先找到专门用来操作文件的FileWriter

FileWriter  fw = new FileWriter("demo.text");

write将字符串并没有直接写到硬盘之中，而是写到流之中了

需要将流中的缓存刷新到目的中，要用flush()方法

流一直存在，可以一直刷新

close关闭流资源，但是关闭之前会

fw.close();也可以刷新缓冲区数据

刷新一次内部缓冲的数据

和flush区别：flush刷新后，流还开着。close刷新后，会关闭流

close一定要有！流一定需要关闭！

IO异常的处理方式

凡是能和机器上的数据发生关系的，都会出现IO异常，无论读写还是创建

文件找不到异常是	IO异常的一个子类。