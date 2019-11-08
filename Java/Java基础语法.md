# Java基础语法

[TOC]

### 标识符

- **定义**

  ​Java对各种变量、方法、类和接口等要素命名时使用的字符序列。

  - *凡是自己可以起名的地方都叫标识符，都遵守标识符的规则。*

- **组成规则**

  - 由字母、下划线`_`、美元符`$`或数字组成；
  - 以字母、下划线`_`、美元符`$`开头，即不以数字开头；
  - 大小写敏感，长度无限制。
  - 不可以使用关键字。

- **命名规范**

  1. 项目名称全部小写；

  2. 包名全部小写，使用`.`连接；

  3. 类名、接口名首字母大写，如果类名由多个单词组成，每个单词的首字母大写；

     ```java
     public class MyFirstClass {
         ...
     }
     ```

  4. 变量名、方法名首字母小写，如果变量名、方法名由多个单词组成，首字母小写，其后单词的首字母大写；

     ```java
     public void toString() {
         int index = 0;
         ...
     }
     ```

  5. 常量名全部大写，使用`_`连接;

     ```java
     public static final String GAME_COLOR="RED";
     ```

- **约定俗成**

  Java标识符的选取应注意“==见名知意==”且不与Java关键字重名。



### 关键字

- **定义**

  Java赋以特定的含义，用作专门用途的字符串。

- **命名规则**

  所有Java关键字都是小写英文。

- **注意事项**

  `goto`和`const`虽然未被使用，但也被作为Java关键字保留。



### 常量

- **定义**

  常量就是不变的数据量，在程序的执行过程中其值不可以发生变化，又称为常量值、字面常量，它是通过数据直接表示的，因此有很多种数据类型。

- **分类**

  Java的常量常用字符串表示，区分为不同的数据类型。

  - 整型常量 `123`
  - 实型常量 `3.14`
  - 字符常量 `'a'`
  - 逻辑常量 `true、false`
  - 字符串常量 `"hello word"`

- “常量”这个名词在其他环境下还会有其他语义，表示==值不可变的变量==。

  - 参见`final`关键字



### 变量

- **定义**

  Java变量是程序中最基本的存储单元，其要素包括变量名、变量类型和作用域。

- **表示**

  Java中每一个变量都有其特定的数据类型，在使用前必须对其声明。

  ```java
  int i = 100;
  float f = 12.3f;
  double d1, d2, d3 = 0.123;
  String s;
  s = "hello world";
  ```

- **Java实质**

  从本质上讲，**变量其实是内存中的一小块区域**，使用变量名来访问这块区域。

  因此，每一个变量使用前必须先申请（声明），然后必须进行赋值（填充内容），才能使用。

- **Java变量的分类**

  - 按声明的位置划分

    - 成员变量

      在方法体外，类体内声明的变量称为成员变量。

    - 局部变量

      方法体内部声明的变量（包括形参）和语句块内部声明的变量称为局部变量。

  - 按所属的数据类型划分

    - 基本数据类型变量
    - 引用数据类型变量



### 数据类型

- **为什么要有数据类型**

  Java是强类型语言，对每一种数据都定义了明确具体的数据类型。

- **数据类型的划分**
  - 基本数据类型
    - 整数类型 byte，short，int，long
    - 浮点类型 float，double
    - 字符型 char
    - 布尔型 boolean
  - 引用数据类型
    - 类 class
    - 接口 interface
    - 数组 array

- **基本数据类型**
  - 逻辑型Boolean
    1. 适应于逻辑运算，一般用于流程控制；
    2. 只允许取值`true`和`false`，不可以非零或零替代`true`和`false`，这点和C不同；

  - 字符型char
    1. 表示一个字符，用`''`括起来。
    2. 采用`Unicode`编码，每个字符占两个字节。

  - 整数类型 
    1. Java整数类型有固定的表数范围和字段长度，不受具体操作系统的影响。
    2. Java整型常量有3种表示形式：
       - 十进制整数：如`12`，`-314`，`0`。
       - 八进制整数：要求以`0`开头，如`012`。
       - 十六进制整数：要求以`0x`或`0X`开头，如`0x12`。
    3. Java有4种类型整型常量：
       - byte	1字节	-128~127
       - short       2字节     -32768~32767
       - int            4字节    
       - long         8字节
    4. Java整型常量默认为`int`型，声明`long`类型常量需要后加`l`或者`L`

    ```java
    int i = 600; //正确
    long l = 88888888888L; //必须加L否则会报错
    ```

  - 浮点类型

    1. Java浮点类型也有固定的表数范围和字段长度，不受具体操作系统的影响。
    2. Java浮点类型有2种表示形式：
       - 十进制数形式，如`3.14`，`314.0`
       - 科学计数法形式，如`3.14e2`，`100E-2`
    3. Java有2种类型浮点型常量：
       - float            4字节
       - double        8字节
    4. Java浮点型常量默认是`double`型，如果要声明一个`float`型常量，则需在后面加`f`或者`F`

    ```java
    double d = 12345.6 //正确
    float f = 12.3f  //必须加f否则会报错
    ```

- **基本数据类型转换**

  - 数据类型按容量大小排序为：

  ```java
  byte,short,char->int->long->float->double
  ```

  - boolean类型不可以转换为其他的数据类型

  - 整型、字符型、浮点型数据在混合运算中可以互相转换。

    - 自动转换：容量小的数据类型自动转换为容量大的数据类型。

    ```java
    double d = 100;
    ```

    - 强制转换：容量大的数据类型转换为容量小的数据类型时，要加上强制转换符，但可能造成精度降低或溢出。

    ```java
    int i = (int) 6.718;  //i的值为6
    
    double d = 3.14;
    int i = (int) d;  //d的值为3
    ```

  - 可以将整型常量直接赋值给`byte`，`short`，`char`类型的变量，而不需要进行强制类型转换，只要不超出其表数范围即可。

    ```java
    byte b = 12;
    char c = 100;
    byte bb = 256;  //error
    short c = -32769;  //error
    ```

  - 多种数据类型混合 运算时，系统首先自动将所有数据类型转换成容量最大的那种数据类型，然后再进行计算。



### **运算符**

- **算数运算符**

  自加++/自减--运算符

```java
++i   //先自加再运算
i++   //先运算再自加

int i = 10;
int j = (i++);  //j=10,i=11
int k = (++i);  //i=12,k=12
```

- **逻辑运算符**

```java
! 逻辑非  & 逻辑与  | 逻辑或  ^ 逻辑异或  && 短路与  || 短路或
```

| a     | b     | !a    | a&b   | a\|b  | a^b   | a&&b  | a\|\|b |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ------ |
| true  | true  | false | true  | true  | false | true  | true   |
| true  | false | false | false | true  | true  | false | true   |
| false | true  | true  | false | true  | true  | false | true   |
| false | false | true  | false | false | false | false | false  |

- **字符串连接符**

  - `+`除了用于算数加法运算外，还可以用于对字符串进行连接操作。

  ```java
  String s = "Hello" + "World";
  ```

  - `+`两侧的操作数只要有一个是`String`类型，系统会自动将另一个操作数转为字符串然后进行连接。

  ```java
  int c = 12;
  System.out.println("c = "+ c );
  ```

  - 当进行打印时，无论何种类型，都自动转为字符串进行打印。

  ```java
  System.out.println(c);
  ```

- **三目条件运算符**

  - 语法格式：`x ? y : z`
  - 其中，`x`是`boolean`类型的表达式。先计算x的值，若为true，则整个三目运算的结果为表达式y的值，否则整个运算结果是表达式z的值。

  ```java
  int score = 80;
  String type = score<60 ? "不及格" : "及格";
  System.out.println(type); //及格
  ```



### 条件语句

- **if语句**

```java
# 1、if
	int i = 5;
	if (i>5){
		System.out.println("if中的判断为true");
	}

# 2、if...else
    int i = 16;
    if (16%2==0){
       System.out.println(i+"是偶数")；
    }else{
       System.out.println(i+"i是奇数")；
    }

# 3、if...else if
    int grade = 75;
    if(grade>80){
        System.out.println("成绩优秀")；
    }else if(grade>70){
        System.out.println("成绩良好")；
    }else if(grade>60){
        System.out.println("成绩及格")；
    }else{
		System.out.println("成绩不及格")；
    }
```

- **switch语句**
  - `switch()`变量类型只能是`int`，`short`，`char`，`byte`和`enum`类型。
  - 当进行case判断时，JVM会自动从上到小扫描，寻找匹配的case，可能存在以下情况：
    1. 若未找到，则执行`default`
    2. 若当前匹配成功的case不存在break，则从当前case开始，依次返回后续case的返回值，直到遇到break，跳出判断。
  - case后面只能是常量，可以是运算表达式。不能是变量，即便变量在之前进行了赋值，JVM依然会报错。

```java
int i = 2;
switch(i){
    case 0:
        System.out.println("0");
        break;
    case 1:
        System.out.println("1");
        break;
    case 2:
        System.out.println("2");
        break;
    default:        
   	    System.out.println("default");
        break;
}
```



### 循环语句

- **for循环**

  1. 使用语法：

  ```java
  for(初始化变量;条件;增量) {
      循环体;
  }
  ```

  2. 各模块解释：

     初始化变量：定义变量，用来控制循环的次数。

     条件：当条件判断为true，执行循环体，条件判断是false，结束循环。

     增量：变量自增情况。

  3. 执行流程：

  ```java
  for(1;2;3) {
  	4;
  }
  第一步，执行1
  第二步，执行2，如果判断结果为true，执行4，如果判断结果为false，跳出循环
  第三步，执行3，然后重复执行第二步
  ```

  4. 代码演示：

  ```java
  //利用for循环，计算1+2+3+...+10的值
  public class ForDemo {
  	public static void main(String[] args){
  		int sum = 0;
          for(int i=1;i<=10;i++){
  			sum = sum + i;
          }
          System.out.println(sum);
      }
  }
  ```

- **while循环**

  1. 使用语法：

  ```java
  初始化表达式；
  while(条件){
  	循环体;
  }
  ```

  2. 执行流程：

  ​        当条件判断是true，就执行循环体，执行完循环体后，程序再次判断while中的条件，,如果条件还是true，继续执行循环体，直到条件是false的时候，跳出循环。

  3. 代码演示：

  ```java
  // 利用while循环，计算1+2+3+...+10的值
  public class WhileDemo {
      public static void main(String[] args) {
      	int sum = 0;
          int i = 1;
          while(i<=10){
              sum = sum + i;
              i++;
          }
          System.out.println(sum);
      }
   }
  ```

- **do while循环**

  1. 使用语法：

  ```java
  do{
      循环体;
  }while(条件)；
  ```

  2. 执行流程：

  ​        先执行一次循环体，然后再判断条件，如果条件为true，继续执行循环体，如果条件为false，循环结束。

  3. 代码演示：

  ```java
  // 利用do while循环，计算1+2+3+...+10的值
  public class DoWhileDemo {
      public static void main(String[] args) {
          int i = 1;
          int sum = 0;
          do{
  			sum = sum + i;
              i++;
          }while(i<=10);
          System.out.println(sum);
      }
  }
  ```

- **嵌套循环**

  1. 定义

  ​        嵌套循环是指在一个循环语句的循环体中再定义一个循环语句的语法结构。while、do…while、for循环语句都可以进行嵌套，并且它们之间也可以互相嵌套，如最常见的在for循环中嵌套for循环。

  2. 基本语法

  ```java
  for(初始化变量;条件;操作表达式){
      ...
      for(初始化变量;条件;操作表达式){
          内循环体;
      }
      ...   
  }
  ```

  3. 各模块解释

     (1) 总的循环次数 =  内循环次数 * 外循环的次数

     (2) 内循环是外循环的循环体

  4. 代码演示

  ```java
  public class ForForDemo {
      public static void main(String[] args){
          /**
          * 打印正三角形
          *
          *		*     
          *		**
          *		***
          *		****
          *		*****
          */
          for(int i=0;i<4;i++){
              for(int j=0;j<i+1;j++){
                  System.out.print("*");
              }
              System.out.println();
          }
      }
  }
  ```

- **break**

  1. 作用

     用于终止某个语句块的执行。

     用在循环体中，可以强行退出循环。

  2. 代码演示

  ```java
  public class BreakDemo{
      public static void main(String[] args){
          int stop = 4;
          for(int i=1;i<6;i++){
              if(i==stop) break;
              System.out.println("i = "+i);    
              }
      }
  }
  
  输出：
  		i = 1
      	i = 2
      	i = 3
  ```

- **continue**

  1. 作用

  ​        用在循环体中，用于终止某次循环过程，跳过循环体中`continue`语句下面未执行的循环，开始下一次循环。

  2. 代码演示

  ```java
  public class ContinueDemo{
      public static void main(String[] args){
          int skip = 4;
          for(int i=1;i<6;i++){
  			if(i==skip) continue;
              System.out.println("i = "+i);
          }
      }
  }
  
  输出：
  		i = 1
      	i = 2
      	i = 3
      	i = 5
  ```

