## 1.让程序休眠

需要加头文件#include <windows.h>

`Sleep(1000);`**休眠**1秒

## 2.清空屏幕

执行系统命令 **cls 清空屏幕**(cmd) 需要#include <stdlib.h>

`system("cls");`



## 3.**==不能用来判断两个字符串是否相等**,需要用到库函数

需要#include <string.h>

`strcmp(password,"123456");`

## 4.**define不是关键字**（是预处理指令）

## 5.scanf_s

//输入数字的时候用空格隔开
`scanf_s("%d%d%d", &a, &b, &c);`

//==输入的时候格式要和scanf_s**一致**==
`scanf_s("%d，%d，%d", &a, &b, &c);`
//输入时就需要输入12，23，42

## 6.math.h

需要#include <math.h>

sqrt(i) 开平方

## 7.时间戳

时间戳//尽量不要放在需要循环的函数体中

#include <time.h>

当前计算机的时间-计算机的起始时间（1970.1.1）

`//time_t time(time_t *timer)`

srand() 需要一个unsigned int

`srand((unsigned int)time(NULL));`

生成1~100之间的随机数

`ret = rand()%100+1;`

## 8.c库函数

## 9.数组

数组中arr【x】【y】 其中列y不能省略  但行x可以省略

## 10.右移操作符

==（对于移位运算符，不要移动负数位，这个是标准未定义的。）==

1）算数右移

右边丢弃，左边补原符号位

2）逻辑右移

右边丢弃，左边补0

## 11、前置++和后置++

int x = a++;
   //先对a先使用，再增加，这样x的值是10；之后a变成11；
   int y = a--;
   //先对a先使用，再自减，这样y的值是11；之后a变成10；

## 12、整型提升

C的整型算术运算总是至少以缺省整型类型的精度来进行的。
为了获得这个精度，表达式中的字符和短整型操作数在使用之前被转换为普通整型，这种转换称为**整型**
**提升。**
**整型提升的意义：**
表达式的整型运算要在CPU的相应运算器件内执行，CPU内整型运算器(ALU)的操作数的字节长度
一般就是int的字节长度，同时也是CPU的通用寄存器的长度。
因此，即使两个char类型的相加，在CPU执行时实际上也要先转换为CPU内整型操作数的标准长
度。
通用CPU（general-purpose CPU）是难以直接实现两个8比特字节直接相加运算（虽然机器指令
中可能有这种字节相加指令）。所以，表达式中各种长度可能小于int长度的整型值，都必须先转
换为int或unsigned int，然后才能送入CPU去执行运算。

```c++
//负数的整形提升
char c1 = -1;
//变量c1的二进制位(补码)中只有8个比特位：
1111111
//因为 char 为有符号的 char
//所以整形提升的时候，高位补充符号位，即为1
//提升之后的结果是：
11111111111111111111111111111111
//正数的整形提升
char c2 = 1;
//变量c2的二进制位(补码)中只有8个比特位：
//00000001
//因为 char 为有符号的 char
//所以整形提升的时候，高位补充符号位，即为0
//提升之后的结果是：
//00000000000000000000000000000001
//无符号整形提升，高位补0
```

## 13、指针

1. 指针类型决定了指针类型进行解引用操作的时候，能够访问空间的大小 如int* p； *p可以访问四个 如果是 double* *类型则是八个字节
2. 指针的类型决定了指针向前或者向后走一步有多大（距离）
3. const int *p; *p不能修改 就相当于p指向的那个值不能修改，但是可以修改p指向的地址；
4. int * const p;*p可以修改，就相当于p指向的那个值可以修改，但是不能修改p指向的地址

## 14、调试最常使用的几个 快捷键

F5
启动调试，经常用来直接跳到下一个断点处。
F9
创建断点和取消断点
断点的重要作用，可以在程序的任意位置设置断点。
这样就可以使得程序在想要的位置随意停止执行，继而一步步执行下去。
F10
逐过程，通常用来处理一个过程，一个过程可以是一次函数调用，或者是一条语句。
F11
逐语句，就是每次都执行一条语句，但是这个快捷键可以使我们的执行逻辑进入函数内部（这是最
长用的）。
CTRL + F5
开始执行不调试，如果你想让程序直接运行起来而不调试就可以直接使用

## 15、编程常见的错误

1. 编译型错误：直接看错误提示信息（双击），解决问题
2. 链接型错误：看错误提示信息，主要在代码中找到错误信息的标识符，然后定位问题所在，一般是标识符名不存在或者拼写错误
3. 运行时错误：借助调试、逐步定位问题



## 16、大小端

大端（存储）模式，是指**数据的低位保存在内存的高地址中**，而数据的高位，保存在内存的低地址
中；
小端（存储）模式，是指**数据的低位保存在内存的低地址中**，而数据的高位,，保存在内存的高地
址中。



## 17、数组指针和指针数组

**数组指针是指针**、**指针数组是数组**

```c
int *p1[10];
int (*p2)[10];
//p1, p2分别是什么？
//p1是指向一个指向有十个整型变量的指针数组 sizeof(p1) == 40
//p2是指向一个数组的指针 sizeof(p2) == 4
```

对于

```c
int arr[10];
```

arr 和 &arr 分别是啥？

```c
#include <stdio.h>
int main()
{
 int arr[10] = { 0 };
 printf("arr = %p\n", arr);
 printf("&arr= %p\n", &arr);
 printf("arr+1 = %p\n", arr+1);
 printf("&arr+1= %p\n", &arr+1);
 return 0;
}
//输出结果如下：
```

![image-20220523111628461](c%E8%AF%AD%E8%A8%80%E7%AC%94%E8%AE%B0.assets/image-20220523111628461.png)

实际上： **==&arr 表示的是数组的地址，而不是数组首元素的地址。==**

分析：

`int（*parr[10]）[5];`

parr是一个数组，该数组有十个元素，每个元素是一个数组指针，该数组指针指向的数组有五个元素，每个元素类型为int

## 18、函数指针

`void (*signal(int , void(*)(int)))(int);`

signal是一个函数声明

signal函数的参数有两个，第一个是interesting类型，第二个是函数指针，该函数指针指向的函数的参数是int 返回类型是void 

signal函数的返回类型是一个函数指针，该函数指针指向的函数的参数是int

**简化：利用typedef**

==1、`typedef void(*pfun_t)(int);`==

==2、`pfun_t signal(int, pfun_t);`==



## 19、函数指针数组

定义：`int (*parr1[10])();`

parr1是数组，其元素是`int(*)()`类型的函数指针

函数指针数组应用：转移表  计算器

```c
#include <stdio.h>
int add(int a, int b)
{
 return a + b;
}
int sub(int a, int b)
{
 return a - b;
}
int mul(int a, int b)
{
 return a*b;
}
int div(int a, int b)
{
 return a / b;
}
int main()
{
 int x, y;
 int input = 1;
    int ret = 0;
    do
   {
        printf( "*************************\n" );
        printf( " 1:add           2:sub \n" );
        printf( " 3:mul           4:div \n" );
        printf( "*************************\n" );
        printf( "请选择：" );
        scanf( "%d", &input);
        switch (input)
       {
         case 1:
              printf( "输入操作数：" );
              scanf( "%d %d", &x, &y);
              ret = add(x, y);
              printf( "ret = %d\n", ret);
              break;
        case 2:
              printf( "输入操作数：" );
              scanf( "%d %d", &x, &y);
              ret = sub(x, y);
              printf( "ret = %d\n", ret);
              break;
        case 3:
              printf( "输入操作数：" );
              scanf( "%d %d", &x, &y);
              ret = mul(x, y);
              printf( "ret = %d\n", ret);
              break;
        case 4:
              printf( "输入操作数：" );
              scanf( "%d %d", &x, &y);
              ret = div(x, y);
              printf( "ret = %d\n", ret);
              break;
        case 0:
                printf("退出程序\n");
 			  break;
        default:
              printf( "选择错误\n" );
              break;
       }
 } while (input);
    
    return 0;
}
```



```c
#include <stdio.h>
int add(int a, int b)
{
           return a + b;
}
int sub(int a, int b)
{
           return a - b;
}
int mul(int a, int b)
{
           return a*b;
}
int div(int a, int b)
{
           return a / b;
}
int main(){
    int x, y;
     int input = 1;
     int ret = 0;
     int(*p[5])(int x, int y) = { 0, add, sub, mul, div }; //转移表
     while (input)
     {
          printf( "*************************\n" );
          printf( " 1:add           2:sub \n" );
          printf( " 3:mul           4:div \n" );
          printf( "*************************\n" );
          printf( "请选择：" );
      scanf( "%d", &input);
          if ((input <= 4 && input >= 1))
         {
          printf( "输入操作数：" );
              scanf( "%d %d", &x, &y);
              ret = (*p[input])(x, y);
         }
          else
               printf( "输入有误\n" );
          printf( "ret = %d\n", ret);
     }
   		return 0;
}
```

**例题：**

`char* my_strcpy(char* dest,const char* src);`

pf是函数指针指向my_strcpy

`char*(*pf)(char*,const char*) = &my_strcpy;`

pfArr[4]是一个函数指针数组 并且存放四个my_strcpy函数的地址

`char*(*PfArr[4])(char*,const char*);`

## 20、指向函数指针数组的指针

指向函数指针数组的指针是一个 **指针** 

指针指向一个 **数组** ，数组的元素都是 **函数指针** ;

```c
void test(const char* str)
{
 printf("%s\n", str);
}
int main()
{
 //函数指针pfun
 void (*pfun)(const char*) = test;
 //函数指针的数组pfunArr
 void (*pfunArr[5])(const char* str);
 pfunArr[0] = test;
 //指向函数指针数组pfunArr的指针ppfunArr
 void (*(*ppfunArr)[5])(const char*) = &pfunArr;
 return 0;
}

```

### summery

```c
int add(int x,int y){
    return x+y;
}
int main(){
    //指针数组
    int *arr[10];
    //数组指针
    int*(*pa)[10] = &arr;
    //函数指针
    int (*pAdd)(int x,int y) = &Add;//Add
    //函数指针的数组
    int(*pArr[5])(int,int);
    //指向函数指针数组的指针
    int(*(*ppArr)[5])(int,int) = &pArr;
    
}
```



## 21、回调函数

**回调函数**就是一个通过函数指针调用的函数。**如果你把函数的指针（地址）作为参数传递给另一个 函数，当这个指针被用来调用其所指向的函数时，我们就说这是回调函数。**回调函数不是由该函数 的实现方直接调用，而是在特定的事件或条件发生时由另外的一方调用的，用于对该事件或条件进 行响应。



将19中转移表的内容进行修改

添加一个函数

```c
void Cala(int(*pf)(int,int)){
	int x = 0;
    int y = 0;
    printf("请输入两个操作数");
    scanf("%d%d",&x,&y);
    printf("%d",pf(x,y));  
}
int main(){
    int input = 0;
    do{
        scanf("%d,&input");
        switch(input){
                case 1:
                	Calc(Add);
                    break;
                case 2:
                	Calc(Sub);
                    break;
                case 3:
                	Calc(Mul);
                    break;
                case 4:
                	Calc(Div);
                    break;
                case 0:
                    break;
        }
    }
}
```

tips：void* 类型不能进行解引用操作

## 22、结构体内存对齐

首先得掌握结构体的对齐规则：

1. 第一个成员在与结构体变量偏移量为0的地址处。

2. 其他成员变量要对齐到某个数字（对齐数）的整数倍的地址处。 

   **对齐数** = 编译器默认的一个对齐数 与 该成员大小的**较小值**。 

   VS中默认的值为8 

3. 结构体总大小为最大对齐数（每个成员变量都有一个对齐数）的整数倍。 

4. 如果嵌套了结构体的情况，嵌套的结构体对齐到自己的最大对齐数的整数倍处，结构体的整体大小就是所有最大对齐数（含嵌套结构体的对齐数）的整数倍。

## 23、字符串相关

### 1、strlen

```cpp
size_t strlen ( const char * str );
```

- 字符串已经 '\0' 作为结束标志，strlen函数返回的是在字符串中 '\0' 前面出现的字符个数（不包 含 '\0' )
- 参数指向的字符串必须要以 '\0' 结束。
- 注意函数的**返回值为size_t**，是无符号的（ 易错 ）
- 学会strlen函数的模拟实现

//模拟实现

```cpp
#include <stdio.h>

int my_strlen(const char* str){
	int count = 0;
    assert(str! = NULL);
    
    while(*str != '\0'){
        count++;
        str++;
    }
    return count;  
}
```



```cpp
#include <stdio.h>
int main()
{
 const char*str1 = "abcdef";
 const char*str2 = "bbb";
 if(strlen(str2)-strlen(str1)>0)
 {
 printf("str2>str1\n");
 } 
 else
 {
 printf("srt1>str2\n");
 }
 return 0;
}
//因为strlen 返回无符号数
//从而 strlen(str2)-strlen(str1) 哪怕是负数 但是最后都会转化为unsigned int 所以都换转化成无符号数 一直输出interestinstr2>str1
```

### 2、strcpy

```CPP
//将source地址的数据拷贝到destination地址处
char* strcpy(char * destination, const char * source );
```

- 源字符串必须以 '\0' 结束。 
- 会将源字符串中的 '\0' 拷贝到目标空间。 
- 目标空间必须足够大，以确保能存放源字符串。
-  目标空间必须可变。 学会模拟实现。

模拟实现

```cpp
char* my_strcopy(char* dest,char* src){
	assert(dest != NULL);
    asser(src != NULL);
    /*while(*src != '\0'){
        *dest = *src;
        dest++;
        src++;
    }
    *dest = *src;*/
    //简化
    char* ret = dest;
    //拷贝src指向的字符串到dest指向的空间，包含'\0'
    while(*dest++ = *src++){
        ;
    }
    //返回目的空间的起始地址
    return ret;
}
```

### 3、strcat

追加字符串

```cpp
char * strcat ( char * destination, const char * source );
```

- 源字符串必须以 '\0' 结束。 
- 目标空间必须有足够的大，能容纳下源字符串的内容。
-  目标空间必须可修改。
-  字符串自己给自己追加，如何？

模拟实现：

```cpp
char* my_strcat(char* dest,const char*src){
    char* ret = dest;
	assert(dest != NULL);
	assert(src);//等价于上述内容
    //找到目的字符串的'\0'
    while(*dest != '\0'){
        dest++;
    }
    //拷贝追加
    while(*dest++ = *src++){
        ;
    }
    return ret;
}
```

### 4、strcmp

比较字符串

```cpp
int strcmp ( const char * str1, const char * str2 );
```

标准规定： 

- 第一个字符串大于第二个字符串，则返回大于0的数字 
- 第一个字符串等于第二个字符串，则返回0 
- 第一个字符串小于第二个字符串，则返回小于0的数字 
- 那么如何判断两个字符串？

模拟实现：

```cpp
my_strcmp(const char* str1,const char*str2){
	assert(str1&&str2);
	while(*str1 == *str2){
		if(*str1 == '\0'){
			return 0;
		}
		str1++;
		str2++;
	}
	if(*str1>*str2)
        return 1;//大于
    else
        return -1;
}
```

### 5、strncpy

```cpp
char * strncpy ( char * destination, const char * source, size_t num );
```

- 拷贝num个字符从源字符串到目标空间。 
- 如果源字符串的长度小于num，则拷贝完源字符串之后，在目标的后边追加0，直到num个。

模拟实现：

```cpp
char* my_strncpy(char* dest,const char* src,int size){
	char* ret = dest;
	while(size&&(*dest++ = *src++)){
        size--;
    }
    if(size)
        while(--size)
            *dest++ = '\0';
    return ret;
}
```

### 6、strncat

```c
char * strncat ( char * destination, const char * source, size_t num );
```

- Appends the first *num* characters of *source* to *destination*, plus a terminating null-character.(追加第一个源地址字符到目的地址，加上一个结束的空字符)
- If the length of the C string in *source* is less than *num*, only the content up to the terminating null-character is copied.（如果c字符串的源地址少于num，只复制结束空字符之前的内容）

模拟实现：

```c
char* my_strncat(char* front,const char* back,int count){
    char* ret = front;
    while(*front++)
        ;
    front--;
    while(count--)
        if(!(*front++ = *back++))
            return ret;
    *front = '\0';
    return(ret);
            
}
```

