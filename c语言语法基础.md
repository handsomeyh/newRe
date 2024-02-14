# 1 c语言简单入门

## 1.1 1个简单的示例：

```c
// #include是预处理命令，用来引入头文件；stdio.h一个头文件
#include <stdio.h>
// 所有的 C 语言程序都需要包含 main() 函数。 代码从 main() 函数开始执行。
int main()
{
    //printf() 用于格式化输出到屏幕。printf() 函数在 "stdio.h" 头文件中声明。
    printf("Hello, world!");
    
    // 终止 main() 函数，并返回值 0。
    return 0;
}
```

## 1.2 c语言注释说明

1. 块注释：/\*.....*/
2. 单行注释：//

## 1.3 c语言的分号（;）

在 C 程序中，分号是语句结束符。也就是说，每个语句必须以分号结束。它表明一个逻辑实体的结束。

## 1.4 标识符

编译原理中有讲，不同语言的标识符各有不同，大致规则如下：

一个标识符以字母 A-Z 或 a-z 或下划线 _ 开始，后跟零个或多个字母、下划线和数字（0-9）。（两个等价类划分的标准）

**标识符作用：**C 标识符是用来标识变量、函数，或任何其他用户自定义项目的名称。

## 1.5 关键字（保留字）

这些保留字不能作为常量名、变量名或其他标识符名称。

大多数数据类型、程序结构

## 1.6 c的空格

数据声明与标识符间一定有空格

## 1.7 c 数据类型

![image-20240105173229742](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240105173229742.png)

### 1.7.1 整数类型

![image-20240105173631709](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240105173631709.png)

**常用：int**

补充：sizeof()函数可以获取对象的存储字节大小，封装在limits.h头文件中

```c
#include <stdio.h>
#include <limits.h>
 
int main()
{
   printf("int 存储大小 : %lu \n", sizeof(int));
   
   return 0;
}
```

### 1.7.2 浮点型

使用前添加头文件float.h

![image-20240105173930063](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240105173930063.png)

### 1.7.3 void型（空）

三种情况使用：

![image-20240105174151984](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240105174151984.png)

### 1.7.4 类型转换

**隐式转换**

隐式类型转换是在表达式中自动发生的，无需进行任何明确的指令或函数调用。它通常是将一种**较小的类型自动转换为较大的类型**

```c
int i = 10;
float f = 3.14;
double d = i + f; // 隐式将int类型转换为double类型
```

![image-20240107112529948](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240107112529948.png)

**显式转换**(更明显)

显式类型转换**需要使用强制类型转换运算符（type casting operator）**，它可以将一个数据类型的值强制转换为另一种数据类型的值。

```c
double d = 3.14159;
int i = (int)d; // 显式将double类型转换为int类型
```

## 1.8 c 变量声明 



## 1.9 存储类

常用：static全局变量

## 1.10 常量



## 1.11 转义字符

| **转义字符** | **含义**       | **转义字符**   | **含义**        |
| ------------ | -------------- | -------------- | --------------- |
| **\n**       | **换行**       | **\t**（常用） | **制表符**      |
| **\v**       | **垂直制表符** | **\b**         | **退格**        |
| **\r**       | **回车**       | **\f**         | **换页**        |
| **\a**       | **响铃**       | **\\**         | **反斜线**      |
| **\’**       | **单引号**     | **\”**         | **双引号**      |
| **\ddd**     | **3位8进制数** | **\xhh**       | **2位16进制数** |

示例：

```c
#include<stdio.h>
#include<stdlib.h>

int main()
{
    
    printf("\101\x42\n");
    printf("\\\\\\\n");
    printf("\'\'\'\"\n");
    printf("\"c\"");
    system("pause");
    return 0;
}
```

结果：

![image-20240105212433666](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240105212433666.png)



# 2 c语言运算符号基础

## 2.1 运算符



## 2.2 数据输出

由特定函数来实现

- 数据输出
  - 格式输出(常用)：printf()
  - 字符输出：putchar()
- 数据输入
  - 格式输入：scanf()
  - 字符输入：getchar()

参考文献：[格式化输入/输出（c语言超详细系列）（一）_c语言中二进制格式化输入输出-CSDN博客](https://blog.csdn.net/m0_74475605/article/details/132049500)

### 2.2.1 格式输出printf()

**基本格式：printf（格式串，表达式1，表达式2，...）**;printf函数被用来显示格式串的内容，并在该串的指定位置插入可能的值。在调用printf时必须提供格式串，格式串后的参数是显示时插入该串的值（可以是常量、变量、以及复杂的表达式）。

**格式串：包含普通字符以及转换说明，其中转换说明以%开头**。**转换说明**是用来表示打印过程中待填充的值的**占位符**，跟在%后面的信息则指定了把数值从计算及内部形式（二进制）转换成想要打印的形式。

例如：**转换说明%d**指定printf函数把int型值从二进制形式转换成十进制形式。

**注意：**

1. 格式串中的普通字符会被完全显现出来，转换说明被表达式的值替换（常规用法），示例如下：

```c
#include<stdio.h>
#include<stdlib.h>

int main()
{
    
    int a=1234;
    float f=123.456;
    char ch='a';
    printf("%8d,%2d\n",a,a);
    printf("%f,%8f,%8.1f,%.2f,%.2e\n",f,f,f,f,f);
    printf("%3c\n",ch);
    system("pause\n");
    return 0;
}
```

结果：

![image-20240106113200584](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240106113200584.png)

2. 转换说明与表达式的数量要匹配

**转换说明的使用（非常重要）：**

转换说明的表示：**%m.pX**

1. m表示要显示的字符总数，通常存在三种情况：

- 如果要**显示的数值所需字符数少于m**，那么值在字段内是**右对齐**的（在值前面加空格凑数），**例如：**%4d将以 123的形式显示数123（123前加一个空格）。
- 如果要**显示的数值数量多于m**，那么**栏宽将会自动扩展**；例如：%4d将以12345的形式显示数12345，而**不会丢失数字**。
- 在**m前加上负号**会导致显示数值左对齐；例如：%-4d将以123 的形式显示123（123的后面有一个空格）

2. p表示精度。

3. X表示转换指定符，一般配合精度使用，例如：

- d——表示**十进制形式的整数**。p指明了待显示数值的最少个数（若缺可在数前补零）

- e——表示指数（**科学计数法**）形式的浮点数。**p指明了小数点后应该出现的数字个数（默认值为6）。如果p为0，则不显示小数点。**

- f——表示浮点数，没有指数，p的含义与说明符e一样。

- g——表示指数形式或者定点十进制形式的浮点数。形式的选择根据数的大小决定，p意味着可以显示的有效数字的最大数量（不是小数点后的数字），与f不同，g的转换将不显示尾随的零（如果g要显示的数值没有小数点后的数字，g就不会显示小数点）。在显示大小适中的数时，g采用定点十进制；在显示非常大或非常小的数时，g则会转换成指数形式。

示例：

```c
#include<stdio.h>
#include<stdlib.h>

int main()
{
    int i;
    float x;
    i = 25;
    x = 200.25f;
    printf("|%d|%5d|%-5d|%5.3d|\n\n",i,i,i,i);
    printf("|%10.3f|%10.3e|%-10g|\n",x,x,x);
    system("pause\n");
    return 0;
}
```

输出：

![image-20240106115542101](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240106115542101.png)

解释：

1. %d—正常输出25。
2. %5d—一共输出5个字符，但是25只有2个字符，就空格填充右对齐。

3. %-5d—同上5个字符，但是加了负号左对齐。

4. %5.3d—一共输出5个字符，并且显示3位少的补0，右对齐。
5. %10.3f—float浮点数，保留3位小数，10个字符位置，右对齐。
6. %10.3e—科学计数法

### 2.2.1 格式输入scanf()

同printf一样，scanf也根据特定的格式进行读取输入。scanf的格式串也可以包含普通字符和转换说明两部分。

*在许多情况下，scanf函数的格式串仅包含转换说明，

例如：scanf（“%d %d”,&i,&j）; 假设用户输入1 -2，scanf函数的作用是读入用户输入信息，然后分别把1 -2赋值给变量i,j。

*需要注意的是：

- 第一：使用scanf函数时，必须检查转换说明的数量是否与输入变量的数量匹配，并检查每个转换是否与变量相对应；
- 第二：&通常放在每个变量前，一定不要忘记，除特殊情况（当本身就表示地址信息时，因为&的意思本就是取地址）。
  

## 2.3 运算符与表达式

### 2.3.1 算术运算符与算术表达式

学习运算符掌握四个要点：

1. 目：运算对象的个数。
2. 功能
3. 优先级
4. 结合方向

算数运算符的内容：

1. 基本运算符：+、-、*、/、%（比较简单）
2. 自增与自减：++、--（考点）

```c
#include<stdio.h>
#include<stdlib.h>

//格式化输入的要点
int main()
{
    //自增运算符++（--也是同理，只是一个先后的问题）
    int j, k, a, b, c;
    j=3;
    k = ++j;//j先自增，再执行赋值
    printf("j=%d, k=%d\n",j,k);
    
    j=3;
    k = j++;//先赋值，再自增
    printf("j=%d, k=%d\n",j,k);

    a=3;
    b=5;
    c = (++a)*b;//a先自增，再相乘
    printf("a=%d, c=%d\n",a,c);

    a=3;
    b=5;
    c = (a++)*b;//先相乘，再自增
    printf("a=%d, c=%d\n",a,c);

    a=3;
    b=5;
    c=a+++b;//a+++b等价于(a++)+b
    printf("a=%d, b=%d, c=%d\n",a,b,c);

    system("pause\n");
    return 0;
}
```

结果：

![image-20240107175043230](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240107175043230.png)

### 2.3.2 赋值运算符与赋值表达式

| 运算符 | 描述                                                         | 实例                            |
| :----- | :----------------------------------------------------------- | :------------------------------ |
| =      | 简单的赋值运算符，把右边操作数的值赋给左边操作数             | C = A + B 将把 A + B 的值赋给 C |
| +=     | 加且赋值运算符，把右边操作数加上左边操作数的结果赋值给左边操作数 | C += A 相当于 C = C + A         |
| -=     | 减且赋值运算符，把左边操作数减去右边操作数的结果赋值给左边操作数 | C -= A 相当于 C = C - A         |
| *=     | 乘且赋值运算符，把右边操作数乘以左边操作数的结果赋值给左边操作数 | C *= A 相当于 C = C * A         |
| /=     | 除且赋值运算符，把左边操作数除以右边操作数的结果赋值给左边操作数 | C /= A 相当于 C = C / A         |
| %=     | 求模且赋值运算符，求两个操作数的模赋值给左边操作数           | C %= A 相当于 C = C % A         |
| <<=    | 左移且赋值运算符                                             | C <<= 2 等同于 C = C << 2       |
| >>=    | 右移且赋值运算符                                             | C >>= 2 等同于 C = C >> 2       |
| &=     | 按位与且赋值运算符                                           | C &= 2 等同于 C = C & 2         |
| ^=     | 按位异或且赋值运算符                                         | C ^= 2 等同于 C = C ^ 2         |
| \|=    | 按位或且赋值运算符                                           | C \|= 2 等同于 C = C \| 2       |

示例：

```c
#include<stdio.h>
#include<stdlib.h>

int main()
{
    int a,b,c,x,y;
    a = 3;
    x = 2;
    y = 3;
    a+=3;//等价于a=a+3,6
    printf("a=%d\n",a);
    x *=y+8;//22
    printf("x=%d,y=%d\n",x,y);
    
    a=12;
    a+=a-=a*a;//a = a - (a*a);a = a+a
    printf("a=%d\n",a);

    a = b = c = 5;
    a = (b = 4);
    printf("a=%d,b=%d\n",a,b);

    system("pause\n");
    return 0;
}
```

结果：

![image-20240107182742602](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240107182742602.png)

### 2.3.3 逗号运算符与逗号表达式



### 2.3.4 关系运算符

| ==   | 检查两个操作数的值是否相等，如果相等则条件为真。             | (A == B) 为假。 |
| ---- | ------------------------------------------------------------ | --------------- |
| !=   | 检查两个操作数的值是否相等，如果不相等则条件为真。           | (A != B) 为真。 |
| >    | 检查左操作数的值是否大于右操作数的值，如果是则条件为真。     | (A > B) 为假。  |
| <    | 检查左操作数的值是否小于右操作数的值，如果是则条件为真。     | (A < B) 为真。  |
| >=   | 检查左操作数的值是否大于或等于右操作数的值，如果是则条件为真。 | (A >= B) 为假。 |
| <=   | 检查左操作数的值是否小于或等于右操作数的值，如果是则条件为真。 | (A <= B) 为真。 |

注意：区分=与==，=是赋值符号，==是恒等于

### 2.3.5 位运算符

| 运算符 | 描述                                                         | 实例                                                         |
| :----- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| &      | 对两个操作数的每一位执行逻辑与操作，如果两个相应的位都为 1，则结果为 1，否则为 0。按位与操作，按二进制位进行"与"运算。运算规则：`0&0=0;    0&1=0;     1&0=0;      1&1=1;` | (A & B) 将得到 12，即为 0000 1100                            |
| \|     | 对两个操作数的每一位执行逻辑或操作，如果两个相应的位都为 0，则结果为 0，否则为 1。按位或运算符，按二进制位进行"或"运算。运算规则：`0|0=0;    0|1=1;    1|0=1;     1|1=1;` | (A \| B) 将得到 61，即为 0011 1101                           |
| ^      | 对两个操作数的每一位执行逻辑异或操作，如果两个相应的位值相同，则结果为 0，否则为 1。异或运算符，按二进制位进行"异或"运算。运算规则：`0^0=0;    0^1=1;    1^0=1;   1^1=0;` | (A ^ B) 将得到 49，即为 0011 0001                            |
| ~      | 对操作数的每一位执行逻辑取反操作，即将每一位的 0 变为 1，1 变为 0。取反运算符，按二进制位进行"取反"运算。运算规则：`~1=-2;    ~0=-1;` | (~A ) 将得到 -61，即为 1100 0011，一个有符号二进制数的补码形式。 |
| <<     | 将操作数的所有位向左移动指定的位数。左移 n 位相当于乘以 2 的 n 次方。二进制左移运算符。将一个运算对象的各二进制位全部左移若干位（左边的二进制位丢弃，右边补0）。 | A << 2 将得到 240，即为 1111 0000                            |
| >>     | 将操作数的所有位向右移动指定的位数。右移n位相当于除以 2 的 n 次方。二进制右移运算符。将一个数的各二进制位全部右移若干位，正数左补 0，负数左补 1，右边丢弃。 | A >> 2 将得到 15，即为 0000 1111                             |

### 2.3.6 逻辑运算符和逻辑表达式

三种逻辑运算符：与或非==》&&，||，！

### 2.3.7 其他运算符

| 运算符        | 描述               | 实例                                 |
| :------------ | :----------------- | :----------------------------------- |
| sizeof()      | 返回变量的大小。   | sizeof(a) 将返回 4，其中 a 是整数。  |
| &（取地址符） | 返回变量的地址。   | &a; 将给出变量的实际地址。           |
| *（指针）     | 指向一个变量。     | *a; 将指向一个变量。                 |
| ? :           | 条件表达式（三目） | 如果条件为真 ? 则值为 X : 否则值为 Y |

# 3 算法与程序基本结构

程序 = 算法+数据结构

算法是解决一个问题的方法和步骤（两种表示：语言表示与流程图表示）

PPT例子：

判定2000~2500年中的每一年是否闰年，将结果输出。已知闰年的条件是：

- 能被4整除，但不能被100整除的年份都是闰年；
- 能被100整除，又能被400整除的年份是闰年。
- 不符合这两个条件的年份不是闰年。

我的答案：

```c
#include <stdio.h>
#include <stdbool.h>
#include <stdlib.h>

bool is_runyear(int year){
    if((year%4==0 && year%100!=0)||(year%100==0 && year%400==0)){
        return true;
    }else{
        return false;
    }  
}

void output_runyear(int year){
    if (is_runyear(year))
    {
        printf("%d是闰年\n",year);
    }else{
        printf("%d不是闰年\n",year);
    }
}

int main(){
    for (int i = 2000; i <= 2500; i++)
    {
        /* code */
        output_runyear(i);
    }
    system("pause");
    return 1;
}
```

## 3.1 程序的三大基本结构

顺序、选择、循环

C语言实现：

1. **分支结构**

```c
1.if结构：
if  /else...if.../else
if(x)<=>if(x!=0)
if(!x)<=>if(x==0)

2.    
switch(){
        case condition1: situation1；break;
        .
        .
        .
        default:situation
}

if与goto实现循环结构
```

注意：

- if ~ else 配对原则：缺省{ }时，else总是和它上面离它最近的未配对的if配对

- 关于switch语句的说明：

  - E1,E2,…En是常量表达式,且值必须互不相同

  - 语句标号作用内，可用break跳出

  - case后可包含多个可执行语句，且不必加{ }

  - switch可嵌套

  - 多个case可共用一组执行语句

2. **循环结构**

```c
1.if goto loop构成循环（不常用）
示例：
#include <stdio.h>
#include <stdlib.h>

//goto loop 实现循环
int main(){
    int sum,i;
    sum = 0;
    i = 1;
    loop:if(i<100){
        sum += i;
        i++;
        goto loop;
    }
    printf("%d\n",sum);
    system("pause");
    return 0;
}

2.while型循环，先判断后循环
int get_sum2(){
    int i,sum=0;
    i=1;
    while (i<=100)
    {
        sum+=i;
        i++;
    }
    return sum;
}
3.do...while实现循环结构，相当于UNTIL，先循环后判断
int get_sum3(){
    int i,sum=0;
    i=1;
    do
    {
        sum+=i;
        i++;
    } while (i<=100);
    
    return sum;
}

4.for型循环
//for实现循环
int get_sum3(){
    int sum=0;
    for (int i = 1; i <= 100; i++)
    {
        sum+=i;
    }
    return sum;
}
```



## 3.2 break与continue

二者结束循环效果不同，break结束跳出整个循环体，然而continue结束整个循环

```c
// 用来区别break与continue的不同
#include<stdio.h>
#include<math.h>
#define PI 3.14159

// 示例1：输出圆的面积，面积大于100时停止
// 使用break
int cal_circle_area(){
    float area;
    for (int r = 0; r <= 10; r++)
    {
       area = PI*r*r;
        if (area>100)
        {
            break;
        }
        printf("r=%d,area=%f",r,area);
    }
    
}

// 示例2：求输入的十个整数中正数的个数及其平均值
// 使用continue
int count_avg(){
    int a,count=0;
    float sum,avg;
    for (int  i = 0; i < 10; i++)
    {
        scanf("%d",&a);
        if (a<=0)
        {
            continue;
        }
        count++;
        sum+=a;
    }
    avg=sum/count;
    printf("%d plus integer's sum :%6.0f\n",count,sum);
    printf("Mean value:%6.2f\n",avg);
  
}

int mian(){
    cal_circle_area();
    printf("\n");
    // count_avg();
    return 1;
}
```



# 4 数组

## 4.1 一维数组

### 4.1.1 概念

数组：用数据名标识，有序数组的集合。

元素：用数组名和下标确定，统一数据类型

注意：

- 定义数组：int a[6];  float f1[5],f2[9],f3[3]；分号结束，逗号隔开
- 错误示例：
  1. 不能用变量定义数组长度
  2. 数组长度必须是正整数！！！

- 存放数据从下标0开始
- 赋值数字个个数不可以超过数组长度

```c
#include <stdio.h>
#include <stdlib.h>

int main(){
    int a[10] = {1,2,3,4,5,6,7,8,9,10};
    // static b数组默认赋值全零
    static int b[5];
    // 遍历数组元素
    for (int i = 0; i < 10; i++)
    {
        printf("%d ",a[i]);
    }

    for (int j = 0; j < 5; j++)
    {
        printf("%d ",b[j]);
    }
}
```

### 4.1.2 一维数组的综合应用

```c
#include <stdio.h>
#include <stdlib.h>
#define SIZE 10

// 读十个整数存入数组，找到其中的最大值和最小值
void find_maxandmin(){
    int nums[SIZE],max,min;
    for (int i = 0; i < SIZE; i++)
    {
        printf("第%d个数字:",i+1);
        scanf("%d",&nums[i]);
    }
    max = min = nums[0];
    for (int i = 0; i < SIZE; i++)
    {
        if (max<nums[i])
        {
            max = nums[i];
        }
        if (min>nums[i])
        {
            min = nums[i];
        }
    }
    printf("最大值为%d\n",max);
    printf("最小值为%d\n",min);

}

// 斐波那契数列输出前20个数字:f1=1,f2=1,fn=fn-1+fn-2
void fibonacci(){
    int f[20] = {1,1};
    for (int i = 2; i < 20; i++)
    {
        f[i] = f[i-1] + f[i-2];
    }
    for (int i = 0; i < 20; i++)
    {
        // 5个数字换一行
        if (i%5 == 0)
        {
            printf("\n");
        }
        // 右对齐
        printf("%12d",f[i]);
    }
    
    
}

// 排序算法：冒泡排序
// 冒泡法排序过程：
// 比较第一个数与第二个数，若为逆序a[0]>a[1]，则交换；然后比较第二个数与第三个数；依次类推，直至第n-1个数和第n个数比较为止——第一趟冒泡排序，结果最大的数被安置在最后一个元素位置上

// 对前n-1个数进行第二趟冒泡排序，结果使次大的数被安置在第n-1个元素位置

// 重复上述过程，共经过n-1趟冒泡排序后，排序结束
void buble_sort(){
    int nums[SIZE] = {7,54,4,11,50,-1,5,-55,6,10};
    int temp;
    for (int i = SIZE-1; i > -1; i--)
    {
        for (int j = 0; j < SIZE; j++)
        {
            temp = nums[j];
            if (nums[j]>nums[j+1])
            {
                nums[j] = nums[j+1];
                nums[j+1] = temp;
            }
        }
        
    }
    for (int i = 0; i < SIZE; i++)
    {
        printf("%d ",nums[i]);
    }
    
}

// 排序算法：简单选择排序
// 首先通过n-1次比较，从n个数中找出最小的， 
// 将它与第一个数交换—第一趟选择排序，
// 结果最小的数被安置在第一个元素位置上
// 再通过n-2次比较，从剩余的n-1个数中找出关键字次小的记录，
// 将它与第二个数交换—第二趟选择排序
// 重复上述过程，共经过n-1趟排序后，排序结束
void select_sort(){
    int nums[SIZE] = {7,54,4,11,50,-1,5,-55,6,10};
    int min,temp,index;
    for (int i = 0; i < SIZE; i++)
    {
        temp = nums[i];
        min = nums[i];
        index = i;
        for (int j = i; j < SIZE; j++)
        {
            if (min>nums[j])
            {
                min = nums[j];
                index = j;
            }
        }
        nums[i]=min;
        nums[index] = temp;
    }
    for (int i = 0; i < SIZE; i++)
    {
        printf("%d ",nums[i]);
    }
}

int main(){
   
    // find_maxandmin();
    // fibonacci();
    // buble_sort();
    // select_sort();
    return 0;
}
```



## 4.2 二维数组及高维数组

| int  a[3] [4] |             |             |             |             |
| ------------- | ----------- | :---------: | ----------- | ----------- |
| **a[**0]      | **a[**0][0] | **a[**0][1] | **a[**0][2] | **a[**0][3] |
| **a[**1]      | **a[**1][0] | **a[**1][1] | **a[**1][2] | **a[**1][3] |
| **a[**2]      | **a[**2][0] | **a[**2][1] | **a[**2][3] | **a[**2][3] |



## 4.3 字符串与字符串数组

字符数组 char c[10],ch[3] [4];

赋值：

1. 逐个赋值

```c
char ch[5]={‘B’,’o’,’y’};
char ch[5]={‘H’,’e’,’l’,’l’,’o’};
```

| B     | o     | y     | \0    | \0    |
| ----- | ----- | ----- | ----- | ----- |
| ch[0] | ch[1] | ch[2] | ch[3] | ch[4] |

1. 字符串常量

```c
char ch[5] = “Boy”;
char ch[6]={“Hello”};
char ch[6]=“Hello”;
char ch[ ]=“Hello”;
```

| H     | e     | l     | l     | o     |
| ----- | ----- | ----- | ----- | ----- |
| ch[0] | ch[1] | ch[2] | ch[3] | ch[4] |

比较  char str[] = "Hello"; 与 char str[] = {h,e,l,l,o},在数组存储时尾部有\0(空字符NULL)

| 0    | 1    | 2    | 3    | 4    | 5    |
| ---- | ---- | ---- | ---- | ---- | ---- |
| H    | e    | l    | l    | o    | \0   |

# 5 函数

## 5.1函数的定义和返回值

1. 库函数需要用#include引入
2. 不指定返回值，默认为整型
3. void不返回值

## 5.2 函数的声明和各种调用

原则：实参和形参个数相等，类型一致，顺序对应

m=max(R1, R2, R3, R4, …);

int max(D1, D2, D3, D4, …)

int D1,D2,D3,D4, …

{…}

## 5.3 函数递归

示例：

```c
#include <stdio.h>

// 求n的阶乘
int fac(int n){
    int res;
    if (n<0)
    {
        printf("n小于0,数据错误");
    }
    else if (n==0 || n==1)
    {
        res = 1;
    }
    else
    {
        res = fac(n-1)*n;
    }
    return res;
}

int main(){
    int n,res;
    printf("输入n的值：");
    scanf("%d",&n);
    res = fac(n);
    printf("%d的阶乘是%d",n,res);
    return 1;
}
```

```c
#include <stdio.h>

// 汉诺塔问题
//计数
static int count=0;
// move:从get柱子-->put柱子
void move(char get,char put){
    printf("%c---->%c\n",get,put);
}

// hanoi:n个盘子，从one,借助two，移到three，
// 自顶向下逐层分解，将one柱上的n个盘子，将上面n-1个看成整体，最后一个看成一个
void hanoi(int n,char one,char two,char three){
    if (n==1)
    {
        move(one,three);
        count++;
    }
    else{
        hanoi(n-1,one,three,two);
        move(one,three);
        count++;
        hanoi(n-1,two,one,three);
    }  
}

int main(){
    int m;
    printf("输入盘子的数量：");
    scanf("%d",&m);
    printf("移动盘子步骤如下：\n");
    hanoi5(m,'A','B','C');
    printf("移动总次数为%d",count);
    return 1;
}

```

## 5.4 函数参数及其传递方式

![image-20240212111708275](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240212111708275.png)

值传递与地址传递

```c
#include <stdio.h>

// 参数传递的两种方式
// 值传递,结果仅仅是形参的值进行了交换,实参的数值不会变化。
void swap1(int a,int b){
    int temp;
    temp = a;
    a = b;
    b = temp;
    printf("a=%d,b=%d",a,b);
}

// 地址传递，此时实参和形参一同变化
void swap2(int *a,int *b){
    int p;
    p = *a;
    *a = *b;
    *b = p;
    printf("a=%d,b=%d",*a,*b);
}

int main(){
    int x=11,y=27;
    // swap1(x,y);
    swap2(&x,&y);
    printf("x=%d,y=%d",x,y);
}
```

数组元素与数组名

```c
#include <stdio.h>

// 参数传递的两种方式
// 值传递,结果仅仅是形参的值进行了交换
void swap1(int a,int b){
    int temp;
    temp = a;
    a = b;
    b = temp;
    printf("a=%d,b=%d",a,b);
}

// 地址传递，此时实参和形参一同变化
void swap2(int *a,int *b){
    int p;
    p = *a;
    *a = *b;
    *b = p;
    printf("a=%d,b=%d",*a,*b);
}


// 比较数组元素与数组名作为函数的参数,
// swap1传数组元素，swap3传数组名,数组名相当于指针
void swap3(int num[]){
    int temp;
    temp = num[0];
    num[0] = num[1];
    num[1] = temp;
}


int main(){
    // int x=11,y=27;
    // swap1(x,y);
    // swap2(&x,&y);
    int num[2] = {1,2};
    swap3(num);
    printf("a[0]=%d,a[1]=%d",num[0],num[1]);
    return 0;
}
```

## 5.5 变量的存储属性

存储属性：

1. 存储器类型：寄存器、静态存储区、动态存储区
2. 生存期：变量在某时刻存在—静态变量与动态变量
3. 作用域：变量在某区域有效—局部变量与全局变量

![image-20240212221116320](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240212221116320.png)

![image-20240212222636348](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240212222636348.png)

### 5.5.1 auto作用域

![image-20240212221701335](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240212221701335.png)



### 5.5.2 局部静态变量具有可继承性

static

```c
#include <stdio.h>

// static变量具有可继承性
int main(){
    void increment(void);
    increment();
    increment();
    increment();
}

void increment(void){
    static int x = 0;
    x++;
    printf("%d\n", x);
}

输出结果：
1
2
3
```

### 5.5.3 extern扩展外部作用域







# 6 指针（c语言的精髓）

## 6.1 指针的概念

**指针**也就是**内存地址**，**指针变量**是用来**存放内存地址的变量**。就像其他变量或常量一样，您必须在使用指针存储其他变量地址之前，对其进行声明。

![image-20240213154521476](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240213154521476.png)

定义指针变量：

```c
int *p;
int num = 10;
p = &num;
```

### 6.1.1 &与*算符

&取地址符，取变量的地址，

*p就可以访问地址的值（指针所指向变量的内容）

两者关系是互为逆运算

i_pointer = &i = &(*i_pointer)

i = *i_pointer = \*(&i)

i_pointer 指针变量，它的内容是地址量

*i_pointer 指针的目标变量，它的内容是数据

&i_pointer 指针变量占用内存的地址

### 6.1.2 直接访问与间接访问

直接访问：用变量的地址去访问变量值

间接访问：通过存放变量地址的另外一个变量去访问变量值



## 6.2 指针变量

i_pointer-->i

定义指针变量：

```c
[存储类型] 数据类型 *指针名
```

注意：

![image-20240213160013079](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240213160013079.png)

### 6.2.1 指针变量的初始化

```c
int i;
int *p=&i;
```

类型必须一致

注意：指针变量必须先赋值再使用

### 6.2.2 零指针(NULL)与空类型指针(void)

零指针

定义：指针变量值为零

表示：int *p=0;

注意：

1. p=NULL与未对p赋值不同
2. 用于避免指针变量的非法引用

空类型指针

定义：不指定所指向单元数据类型的指针变量

表示：void *p;

注意：使用时要进行强制类型转换，如下图：

![image-20240213161431904](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240213161431904.png)

指针变量作为函数参数——地址传递，特点：共享内存，双向传递（形参实参值会一起变化）

## 6.3 指针与数组

数组名是表示数组首地址的地址常量

```c
int array[10];
int *p;
p = &array[0];<=>p=array;
int *p=&array[0];
int *p=array;
```

## 6.4 指针的运算

### 6.4.1 赋值运算

1. p=&a  将变量a的地址赋值给p
2. p=array  将array首地址赋值给p
3. p=&array[i];  将数组第i元素地址赋值给p
4. p1=p2; 指针变量p2值赋给p1
5. 整型变量

### 6.4.2 算术运算

(1) p ± i <=> p± i×d (i整型数，变量字节数)

(2) p++, p--, p+i, p-i, p+=i, p-=i 等

(3) 若p1与p2指向同一数组，则 p1-p2=两指针间元素个数 <=> (p1-p2)/d

(4) p1+p2 无意义

### 6.4.3 关系运算

(1) p1<p2  表示p1指的元素在前

(2) p1>p2  表示p1指的元素在后

(3) p1==p2 表示p1与p2指向同一元素

(4) 若p1与p2指向不同数组，比较无意义

(5) p==NULL或p!=NULL

### 6.4.4 数组元素的表示

[]变址运算符，a[i]  <=>  *(a+i)

```c
int array[6];
int *p=array;

此时：
a[i]<=>p[i]<=>*(p+i)<=>*(a+i)
```

![image-20240213184519337](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240213184519337.png)

```c
#include <stdio.h>

int main(){
    int a[]={1,2,3,4,5,6,7};
    int y,*p=&a[1];
    // 1.--ps使得p指向a[0];
    // 2.++使得y先被赋值为1，再将a[0]+1
    y = (*--p)++;
    printf("%d\n",y);
    printf("%d\n",a[0]);

    return 0;
}
```

```
#include <stdio.h>

int main(){
    int i,*p,a[7];
    p=a;
    for ( i = 0; i < 7; i++)
    {
        scanf("%d",p+i);
    }
    printf("\n");

    for (i = 0; i < 7; i++)
    {
        printf("%d\n",*p);
        p++;
    }
    return 0;
}
```

```c
#include <stdio.h>

// 将数组a中的n个整数按相反顺序存放(地址传递的方式)
// 1.传递数组名作为参数
// 思想：双指针，一个在头，一个在尾，向中间移动交换位置
void inv1(int x[], int n){
    int i,j,temp,mid=(n-1)/2;
    for ( i = 0; i <= mid; i++)
    {
        j = n-1-i;
        temp = x[i];
        x[i] = x[j];
        x[j] = temp;
    }
}

// 指针作为参数，通过索引的方式进行交换
void inv2(int *p,int n){
    int i,j,temp,mid=(n-1)/2;
    for ( i = 0; i <= mid; i++)
    {
        j = n-1-i;
        temp = p[i];
        p[i] = p[j];
        p[j] = temp;
    }
}

// 完全通过指针的方式进行交换
void inv3(int *a,int n){
    int temp,*m,*i,*j,mid = (n-1)/2;
    i=a;
    j=a-1+n;
    m=a+mid;
    for (; i <= m; i++,j--)
    {
        temp = *i;
        *i = *j;
        *j = temp;
    }
    
}

int main(){
    // 实参也可以通过指针来实现
    int i,a[10]={3,7,9,11,0,6,7,5,4,2};
    // inv1(a,10);
    // inv2(a,10);
    inv3(a,10);
    printf("经过逆置后的数组：\n");
    for ( i = 0; i < 10; i++)
    {
        printf("%d ",a[i]);
    }
    return 0; 
}
```



# 7 结构体与共用体

常用于自定义数据结构：树，图，节点，哈夫曼树，堆，栈，线性表

构造类型

![image-20240214104823381](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240214104823381.png)

## 7.1 结构体的定义（struct）：

```c
#include <stdio.h>

// 自定义student结构体
struct student
{
    char name[20];// 姓名
    unsigned int number;// 学号
    char sex;// 性别
    char ethnicity[8];// 民族
    float score[3];// 分数
};

struct student stu1, *stu, stu3[20];
```

无结构体名定义形式

```c
struct  {}stu1,*stu2,stu3[20]
```

## 7.2 结构体变量的引用

```c
定义：
struct student
{
    int num;
    char name[20];
    struct data
    {
        int month;
        int day;
        int year;
    } birtday;
}stu1,*stu2;

引用：
stu1 != stu2;
stu1.num=10;    stu2->num=12;   (*stu2).num = 12;
stu1.birthday.mont=12;
stu2 = &stu1;
```

## 7.3 结构体变量的初始化

```c
方式1：
#include <stdio.h>

// 自定义student结构体
struct student
{
    int num;
    char name[20];
    char sex;
    int age;
    char addr[30];
};

struct student stu1 = {112,"yinhang",'M',19,"200 Beijing Road"};
```

```
方式2：
struct
{
    int num;
    char name[20];
    char sex;
    int age;
    char addr[30];
}stu1 = {112,"yinhang",'M',19,"200 Beijing Road"};

```

结构体数组：

```c
#include <stdio.h>

// 自定义student结构体
struct student
{
    int num;
    char name[20];
    char sex;
    int age;
    char addr[30];
};

struct student stu1[] = {{112,"yinhang",'M',19,"200 Beijing Road"},
                        {112,"yinhang",'F',19,"200"}};
```

```
#include <stdio.h>

// 统计候选人选票
struct person
{
    int id;
    char name[20];
    int count;
}leader[3]={{1, "Li", 0}, {2, "Zhang", 0}, {3, "Wang", 0}};

int main(){
    int i,j,num;
    printf("--------------------------------\n");
    printf("1--Li  2--Zhang 3--Wang\n");
    printf("--------------------------------\n");
    printf("请选择候选人为其投票(仅需要输入名字前的数字):\n");
    for (int i = 0; i < 20; i++)
    {
        scanf("%d",&num);
        for (int j = 0; j<3; j++)
        {
            if (leader[j].id == num)
            {
                leader[j].count++;
                break;
            }
        }
    }
    printf("投票情况如下:\n");
    for ( i = 0; i < 3; i++)
    {
        printf("%d--%s 票数:%d\n",leader[i].id,leader[i].name,leader[i].count);
    }
    

}
```

![image-20240214113900597](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240214113900597.png)

数组存储数据：

- 内存中连续存放

- 大小固定，定义时长度为整型常量

- 不能动态分配

解决方法：动态链表

## 7.4 共用体(union)

```c
union data
{
    int i;
    char ch;
    float f;
};

union data a,b,c,*p,d[3];
```

**共用体变量任何时刻只有一个成员存在**

几个不同类型的变量共用一段内存

共用体变量定义分配内存 长度 = 最长成员所占字节数

示例：

```c
#include <stdio.h>

// 共用体：将一个整数按字节输出
union int_char 
{
    int i;
    char c[2];
} x;

int main(void){
    x.i = 24897;
    printf("i=%d\n", x.i);
    printf("c[0]=%o,c[1]=%o,c[0]=%c,c[1]=%c", x.c[0], x.c[1], x.c[0], x.c[1]);
    
}
```





## 7.5 typedef定义新类型（新命名类型）







# 8 编译预处理、位运算与文件

## 8.1 编译预处理

三种预编译命令：

1. 宏定义：#define  #undef
2. 文件包含：#include
3. 文件编译：#if   #else    #endif

示例：

```c
#define YES 1
#define NO 0
#define PI 3.1415926
#define OUT printf("hello")
```

宏的作用域

```c
#define YES 1
main(){

}
#undef YES
```

通过宏简化输入输出：

```c
/*format*/
#define PR printf
#define NL "\n"
#define D "%d"
#define D1 D NL
#define D2 D D NL
#define D3 D D D NL
#define D4 D D D D NL
#define S "%s"
```

```c
#include <stdio.h>
#include "format.h"

int main(void) {
    PR(D1, 1);
    PR(D2, 1, 2);
    PR(D3, 1, 2, 3);
    PR(D4, 1, 2, 3, 4);
    PR(S, "Hello, World!");
    return 0;
}
```

注意：

![image-20240214161835575](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240214161835575.png)

![image-20240214161846715](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240214161846715.png)

![image-20240214161857549](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240214161857549.png)

宏定义可以实现一些简单的函数,取较大值

```c
#define MAX(x,y) x>y?x:y
```

## 8.2 位运算

### 8.2.1 按位与&（AND）

运算规则：有0则0，全1则1

![image-20240214162729738](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240214162729738.png)

用于：（1）清零

​			（2）取数中某些指定位

### 8.2.2 按位或|（OR）

![image-20240214163049079](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240214163049079.png)

用于：将某指定位设置为1

### 8.2.3 按位异或（^）（XOR）

![image-20240214163132173](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240214163132173.png)

用于：（1）使得特定位翻转

​			（2）与0异或保持原值和

​			（3）交换两值不用临时变量

### 8.2.4 按位取反（~）（NOT）

![image-20240214201422139](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240214201422139.png)

## 8.3 文件操作c语言

文件概念：储存在外部介质上数据的集合，操作系统数据管理的单位。

![image-20240214201752654](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240214201752654.png)

### 8.3.1 c语言对文件的操作途径

stdio.h中文件类型结构体

```c
typedef   struct
{
     int      _fd;         //文件号
     int      _cleft;     //缓冲区中剩下的字符数
     int      _mode;   //文件操作方式
     char   *_next;   //文件当前读写位置
     char   *_buff;   //文件缓冲区位置
} FILE;
```

定义文件指针

```c
FILE *fp;
```

C语言对文件的操作步骤：

第一步：声明指针变量

```c
FILE *fp;
```

第二部：打开文件

```c
fp = fopen("c:\\Turboc2\\test.dat","r");
```

文件打开方式：

![image-20240214203224449](C:\Users\20866\AppData\Roaming\Typora\typora-user-images\image-20240214203224449.png)

第三步：对文件进行读、写、定位

```c
fprintf( fp, “%d,%6.2f”, i, t );  //将i和t按%d,%6.2f格式输出到fp文件
fscanf( fp, “%d,%f”, &i, &t ); //若文件中有3,4.5  ,则将3送入i, 4.5送入t
```

第四步：关闭文件fclose

```c
fclose(fp);
```

示例：

```c
#include <stdio.h>
#include <stdlib.h>

// 从键盘按格式输入数据存到磁盘文件中去
// w只读，r只写
int main(){
    char s[80],c[80];
    int a,b;
    FILE *fp;
    if ((fp=fopen("test","w"))==NULL)
    {
        puts("can't open test file");
        exit(-1);
    }
    fscanf(stdin,"%s%d",s,&a);// 从键盘输入
    fprintf(fp,"%s %d",s,a);// 写入文件
    fclose(fp);
    if ((fp=fopen("test","r"))==NULL)
    {
        puts("can't open test file");
        exit(-1);
    }
    fscanf(fp,"%s%d",c,&b); // 从文件读入
    fprintf(stdout,"%s %d",c,b); // 向屏幕输出
    fclose(fp);

}
```





# 9 c语言算法题中遇到的一些点

## 9.1 取绝对值

开头导包

```c
#include<math.h>
```

不同数据类型需要不同的函数

- **int->abs()**
- **long ->labs()**
- **float ->fabsf()**
- **double->fabs()**
- **long double->fabsl()**

