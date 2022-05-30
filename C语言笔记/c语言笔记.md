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
- 目标空间必须可变。 学会模拟实现。

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
- 目标空间必须可修改。
- 字符串自己给自己追加，如何？

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

### 7、strncmp

```c
int strncmp ( const char * str1, const char * str2, size_t num );
```

![image-20220525085220816](c%E8%AF%AD%E8%A8%80%E7%AC%94%E8%AE%B0.assets/image-20220525085220816.png)

### 8、strstr

```c
char * strstr ( const char *str1, const char * str2);
```

- Returns a pointer to the first occurrence of str2 in str1, or a null pointer if str2 is not part of str1.

模拟实现：

```c
#include <assert.h>
char * my_strstr ( const char *str1, const char * str2){
    assert(p1);
    assert(p2);
    char *s1 = p1;
    char* s2 = p2;
    char* cur = p1;
    if(*p2 == '\0') return p;
    while(*cur){
        s1 = cur;
        s2 = p2;
        while((*s1 == *s2)&&(*s1 != '\0')&&(*s2 != '\0')){
            s1++;
            s2++;
        }
        if(*s2 == '\0'){
            return cur;
        }
        cur++;
    }
    return NULL;
}
```



### 9、strtok

```c
char * strtok ( char * str, const char * sep );
```

- sep参数是个字符串，定义了用作分隔符的字符集合 
- 第一个参数指定一个字符串，它包含了0个或者多个由sep字符串中一个或者多个分隔符分割的标记。
- strtok函数找到str中的下一个标记，并将其用 \0 结尾，返回一个指向这个标记的指针。（注： strtok函数会改变被操作的字符串，所以在使用strtok函数切分的字符串一般都是临时拷贝的内容 并且可修改。）
- strtok函数的第一个参数不为 NULL ，函数将找到str中第一个标记，strtok函数将保存它在字符串 中的位置。 strtok函数的第一个参数为 NULL ，函数将在同一个字符串中被保存的位置开始，查找下一个标 记。
- 如果字符串中不存在更多的标记，则返回 NULL 指针。



### 10、strerror

```c
char * strerror ( int errnum );
```

返回错误码，所对应的错误信息。



#### 字符分类函数

![image-20220525102931905](c%E8%AF%AD%E8%A8%80%E7%AC%94%E8%AE%B0.assets/image-20220525102931905.png)

### 11、memcpy

```c
void * memcpy ( void * destination, const void * source, size_t num );
```

![image-20220526092855531](c%E8%AF%AD%E8%A8%80%E7%AC%94%E8%AE%B0.assets/image-20220526092855531.png)

模拟实现：

```c
void * memcpy ( void * dst, const void * src, size_t count)
{
        void * ret = dst;
   assert(dst);
   assert(src);
        /*
         * copy from lower addresses to higher addresses
         */
        while (count--) {
                *(char *)dst = *(char *)src;
                dst = (char *)dst + 1;
                src = (char *)src + 1;
       }
        return(ret);
}
```



### 12、memmove

```c
void * memmove ( void* destination, const void * source, size_t num );
```

![image-20220526092949466](c%E8%AF%AD%E8%A8%80%E7%AC%94%E8%AE%B0.assets/image-20220526092949466.png)

模拟实现：

```cpp
void * memmove ( void * dst, const void * src, size_t count)
{
        void * ret = dst;
    //从q
        if (dst <= src || (char *)dst >= ((char *)src + count)) {
                /*
                 * Non-Overlapping Buffers
                 */
                 while (count--) {
                        *(char *)dst = *(char *)src;
                        dst = (char *)dst + 1;
                        src = (char *)src + 1;
               }
       }
        else {
                /*
                 * Overlapping Buffers
                 * copy from higher addresses to lower addresses
                 */
                dst = (char *)dst + count - 1;
                src = (char *)src + count - 1;
                while (count--) {
                        *(char *)dst = *(char *)src;
                        dst = (char *)dst - 1;
                        src = (char *)src - 1;
               }
       }
        return(ret);
}
                 
```



### 13、memcmp

```c
int memcmp ( const void * ptr1, 
 			const void * ptr2, 
			size_t num );
```

![image-20220526093033847](c%E8%AF%AD%E8%A8%80%E7%AC%94%E8%AE%B0.assets/image-20220526093033847.png)

## 24、位段

位段的声明和结构是类似的，有两个不同： 

1. 位段的成员==必须==是 **int、unsigned int 或signed int** 
2. 位段的成员名后边有**一个冒号和一个数字**



位段的内存分配

1. 位段的成员可以是 int unsigned int signed int 或者是 char （属于整形家族）类型 
2. 位段的空间上是按照需要以4个字节（ int ）或者1个字节（ char ）的方式来开辟的
3.  位段涉及很多不确定因素，位段是不跨平台的，注重可移植的程序应该避免使用位段

![image-20220530091828817](c%E8%AF%AD%E8%A8%80%E7%AC%94%E8%AE%B0.assets/image-20220530091828817.png)

**总结：** 

跟结构相比，位段可以达到同样的效果，但是可以很好的节省空间，但是有跨平台的问题存在。

## 25、枚举和共用体

枚举类型的定义（枚举为常量）

```cpp
enum Day//星期
{
 Mon,
 Tues,
 Wed,
 Thur,
 Fri,
 Sat,
 Sun
};
enum Sex//性别
{
 MALE,
 FEMALE,
 SECRET
}；
enum Color//颜色
{
 RED,
 GREEN,
 BLUE
};
```

**枚举的优点：** 

1. 增加代码的可读性和可维护性 
2. 和#define定义的标识符比较枚举有类型检查，更加严谨。
3. 防止了命名污染（封装） 
4. 便于调试 
5. 使用方便，一次可以定义多个常量

**联合类型的定义** 

​		**联合**也是一种特殊的自定义类型 这种类型定义的变量也包含一系列的成员，特征是这些成员公用同一块空间（所以联合也叫共用体）。

```cpp
//联合类型的声明
union Un
{
 char c;
 int i;
};
//联合变量的定义
union Un un;
//计算连个变量的大小
printf("%d\n", sizeof(un));
```

 **联合特点：**

​		联合的成员是共用同一块内存空间的，这样一个联合变量的大小，至少是最大成员的大小（因为联 合至少得有能力保存最大的那个成员）。26、



## 26、动态内存分配

为什么要动态内存分配

1. 空间开辟大小是固定的。
2. 数组在申明的时候，必须指定数组的长度，它所需要的内存在编译时分配。 

​		但是对于空间的需求，不仅仅是上述的情况。有时候我们需要的空间大小在程序运行的时候才能知道， 那数组的编译时开辟空间的方式就不能满足了。 这时候就只能试试动态存开辟了。



**malloc**和**free**

```c++
void* malloc (size_t size);
```

这个函数向内存**申请**一块连续可用的空间，并返回指向这块空间的指针。 

- 如果开辟成功，则返回一个指向开辟好空间的指针。
-  如果开辟失败，则返回一个NULL指针，因此malloc的返回值一定要做检查。 
- 返回值的类型是 void* ，所以malloc函数并不知道开辟空间的类型，具体在使用的时候使用者自己 来决定。
-  如果参数 size 为0，malloc的行为是标准是未定义的，取决于编译器。

```c
void free (void* ptr);
```

free函数用来**释放**动态开辟的内存。 

- 如果参数 ptr 指向的空间不是动态开辟的，那free函数的行为是未定义的。
-  如果参数 ptr 是NULL指针，则函数什么事都不做。



**calloc**

```c
void* calloc (size_t num, size_t size);
```

- 函数的功能是为 num 个大小为 size 的元素开辟一块空间，并且把空间的每个字节初始化为0。
-  与函数 malloc 的区别只在于 calloc 会在返回地址之前把申请的空间的每个字节初始化为全0。



**realloc**

```c
void* realloc (void*ptr, size_t size);
```

realloc函数的出现让动态内存管理更加灵活。 

有时会我们发现过去申请的空间太小了，有时候我们又会觉得申请的空间过大了，那为了合理的时 候内存，我们一定会对内存的大小做灵活的调整。那 realloc 函数就可以做到对动态开辟内存大小 的调整。

ptr 是要调整的内存地址 size 调整之后新大小 返回值为调整之后的内存起始位置。 这个函数调整原内存空间大小的基础上，还会将原来内存中的数据移动到 新 的空间。 

realloc在调整内存空间的是存在两种情况：

![image-20220530113224174](c%E8%AF%AD%E8%A8%80%E7%AC%94%E8%AE%B0.assets/image-20220530113224174.png)

**常见的动态内存错误：**

![image-20220530113523900](c%E8%AF%AD%E8%A8%80%E7%AC%94%E8%AE%B0.assets/image-20220530113523900.png)

![image-20220530113532632](c%E8%AF%AD%E8%A8%80%E7%AC%94%E8%AE%B0.assets/image-20220530113532632.png)

![image-20220530113550231](c%E8%AF%AD%E8%A8%80%E7%AC%94%E8%AE%B0.assets/image-20220530113550231.png)







**C/C++程序内存分配的几个区域：**



![image-20220530113812169](c%E8%AF%AD%E8%A8%80%E7%AC%94%E8%AE%B0.assets/image-20220530113812169.png)

1. 栈区（stack）：在执行函数时，函数内局部变量的存储单元都可以在栈上创建，函数执行结 束时这些存储单元自动被释放。栈内存分配运算内置于处理器的指令集中，效率很高，但是 分配的内存容量有限。 栈区主要存放运行函数而分配的局部变量、函数参数、返回数据、返 回地址等。
2. 堆区（heap）：一般由程序员分配释放， 若程序员不释放，程序结束时可能由OS回收 。分 配方式类似于链表。 
3. 数据段（静态区）（static）存放全局变量、静态数据。程序结束后由系统释放。
4. 代码段：存放函数体（类成员函数和全局函数）的二进制代码

有了这幅图，我们就可以更好的理解在《C语言初识》中讲的static关键字修饰局部变量的例子了。 

- 实际上普通的局部变量是在栈区分配空间的，栈区的特点是在上面创建的变量出了作用域就销毁。 
- 但是被static修饰的变量存放在数据段（静态区），数据段的特点是在上面创建的变量，直到程序 结束才销毁 所以生命周期变长。

## 27、柔性数组

```c
typedef struct st_type
{
 int i;
 int a[0];//柔性数组成员
}type_a;

//有些编译器会报错无法编译可以改成：
typedef struct st_type
{
 int i;
 int a[];//柔性数组成员
}type_a;

```

**特点：**

- 结构中的柔性数组成员前面必须至少一个其他成员。 
- sizeof 返回的这种结构大小不包括柔性数组的内存。 
- 包含柔性数组成员的结构用malloc ()函数进行内存的动态分配，并且分配的内存应该大于结构的大 小，以适应柔性数组的预期大小。

**使用：**

```c
//代码1
int i = 0;
type_a *p = (type_a*)malloc(sizeof(type_a)+100*sizeof(int));
//业务处理
p->i = 100;
for(i=0; i<100; i++)
{
 p->a[i] = i;
}
free(p);
```

**优势：**

==第一个好处是：==

方便内存释放 如果我们的代码是在一个给别人用的函数中，你在里面做了二次内存分配，并把整个结构体返回给 用户。用户调用free可以释放结构体，但是用户并不知道这个结构体内的成员也需要free，所以你 不能指望用户来发现这个事。所以，如果我们把结构体的内存以及其成员要的内存一次性分配好 了，并返回给用户一个结构体指针，用户做一次free就可以把所有的内存也给释放掉。

 ==第二个好处是：==

这样有利于访问速度. 连续的内存有益于**提高访问速度**，也有益于**减少内存碎片**。（其实，我个人觉得也没多高了，反正 你跑不了要用做偏移量的加法来寻址）
