# java study

## 数据类型

### 基本数据类型

​	整形： byte（1位） short（2位） int（4位） long（8位）

​	浮点类型：float（4位）double（8位）

​	其他：char（2位）boolean（1或4位） 

​	float精确到后8位，double精确到后17位。整形默认int，浮点默认double。int转float，long转double会丢失精度。

### 访问权限

|      | public | protected | default | private |
| ---- | ------ | --------- | ------- | ------- |
| 本类 | Y      | Y         | Y       | Y       |
| 同包 | Y      | Y         | Y       | N       |
| 子类 | Y      | Y         | N       | N       |
| 全部 | Y      | N         | N       | N       |

### Bigdecimal 数据初始化

```java
Bigdecimal bigdecimal1 = new Bigdecimal("0.1");
Bigdecimal bigdecimal2 = new Bigdecimal(0.1);
sout(bigdecimal1.compareTo(bigdecimal2)==0);//显示false，因为二进制不能完全表示0.1，bigdecimal1只能是0.1的约等数。
```

### 符号数

​	java保存的都是有符号数。

### 克隆（clone）

​	浅拷贝：对基本数据类型进行值传递，对引用数据类型进行引用传递般的拷贝，此为浅拷贝。

​	深拷贝：对基本数据类型进行值传递，对引用数据类型，创建一个新的对象，并复制其内容，此为深拷贝。

​	常用工具类：Apatch和Spring的BeanUtils

​	推荐使用**Spring的BeanUtils**。Apatch不仅只能浅拷贝，而且加了很多的校验，性能不行；Spring的工具类可以自动忽视名称不相等的成员变量，但是成员变量的类型必须相等。

### 泛型

​	泛型，即“参数化类型”。泛型的参数类型只能是类类型，不能是简单类型。

#### 1、泛型实例（泛型类）

```java
//此处T可以随便写为任意标识，常见的如T、E、K、V等形式的参数常用于表示泛型
//在实例化泛型类时，必须指定T的具体类型
public class Generic<T>{ 
    //key这个成员变量的类型为T,T的类型由外部指定  
    private T key;
    public Generic(T key) { //泛型构造方法形参key的类型也为T，T的类型由外部指定
        this.key = key;
    }
    public T getKey(){ //泛型方法getKey的返回值类型为T，T的类型由外部指定
        return key;
    }
}
```



	#### 2、泛型只在编译阶段有效

```java
List<String> stringArrayList = new ArrayList<String>();
List<Integer> integerArrayList = new ArrayList<Integer>();

Class classStringArrayList = stringArrayList.getClass();
Class classIntegerArrayList = integerArrayList.getClass();

sout(classStringArrayList.equals(classIntegerArrayList));//输出true
```

运行时不存在泛型（泛型检查），只有在编译时有效，编译的时候就会转换成具体的类型



## 类

### 构造函数

​	当有<u>自定义构造函数</u>后，<u>默认构造函数</u>失效

### final修饰符

​	final修饰变量的时候，必须初始化，且只能初始化一次。如果给final变量多次赋值，除第一次赋值外，后续的赋值都会编译报错。

​	final修饰类的时候，类不能够被继承。final修饰方法的时候，方法不能被重写。

### 对象转换

​	超类可以引用子类；子类不能引用超类，如果子类要想引用超类，必须进行类型转换（超类的实质是指定的合法的子类）。类型转换关键字 instanceof。

​	子类实例 instanceof 超类，得到ture；超类实例 instanceof 子类，得到false；超类可以代表子类，子类不能代表超类。

### 默认初始值

​	静态域和实例域如果没有在构造函数中赋值，那么编译器会自动赋值；数值类为0，布尔值为false，对象为null。方法中的域必须初始化，不然<u>任何用到该变量的地方编译报错</u>。

​	初始化代码块先于构造函数运行。超类构造函数先于子类构造函数运行。this()调用本类构造方法，supper()调用超类构造方法。

​	如果超类没有无参构造方法，那么子类必须显式调用超类构造方法。

​	超类必须先于子类构造完成，子类构造的时候，先执行初始化代码块中的内容，再执行构造方法里面的内容。所以new一个实例，方法执行顺序为：超类构造方法-子类初始化代码块-子类构造方法。

​	构造函数中必须显式调用supper()：超类有且只有<u>有参构造函数</u>

### 多态

​	一个超类能够指向多个不同子类，称为多态。

​	类的强制类型转换只能在继承层次内进行。

### 抽象类

​	一个类中有抽象方法则必须声明为抽象类；

​	抽象类不能被实例化；

​	抽象类可以没有抽象方法；

### Objec

所有类都是objec的子类；

#### Object方法

​	equals方法：另外一个实例非空，class相等，属性值相等。

​	hashCode方法：如果没有重写hashCode方法，那么hashCode值为对象的存储地址。hashCode方法返回一个整数（可以是正、负数）

​	toString方法：

​	注意：hashCode相等，equals方法不一定相等；equals方法相等，hashCode方法一定相等。尽量保持<u>hashCode相等，equals就相等</u>，有利于提高hash对象的存储读取效率。

## 多态

### 成员变量

​	类的成员变量不具备多态性。相同名称的成员变量会生成两份：父类（接口）一份，子类（实现类一份）。

```java
Father father = new Son();
sout(father.name)//获取的是father的成员变量name
sout(((Son)father).name)//获取的是son的成员变量name
```

### 方法

​	类的方法具备多态性

#### 1、可见性

​	重写方法的可见性必须大于父类方法的可见性（里氏代换原则：任何基类可以出现的地方，子类一定可以出现）；接口方法的修饰符必须是public的，成员变量默认public static final，方法默认public abstract。

#### 2、多态性

```java
Father father = new Son();
sout(father.getName());
sout(((Son)father).getName());//两者都是获取的son的name，因为getName()方法调用的是Son的getName()方法
```

### 方法调用

classA A = new classB(); classA是classB的超类，当调用A.methodM()的时候，如果classB有methodM，那么使用B的方法，如果没有，那么使用classA的方法。

子类重写父类的方法，子类的方法的可见性比父类方法的可见性高。

### 自动装箱拆箱

自动装箱和自动拆箱是在<u>编译</u>阶段实现的。

#### 自动装箱

自动装箱指的是将<u>基本类型</u>的值赋值给<u>包装类型</u>

```java
Integer i = 1;
#在编译的时候自动装箱
Integer i = Integer.valueOf(1)
```

#### 自动拆箱

自动拆箱也是在编译的时候将<u>包装类型</u>的值赋值给<u>基本类型</u>

```java
int i = 1;
#在编译的时候自动装箱
int i = Integer.valueOf(1)
```

https://www.cnblogs.com/wgblog-code/p/11362544.html

### 静态代码块

```java
static{

}
```

随着类的编写