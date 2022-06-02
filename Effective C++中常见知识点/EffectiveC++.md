# Effective 笔记

## 条款2：尽量以const、enum、inline替换#define

![img](EffectiveC++.assets/9DACB8B9FEE2C351A6E115FE581440E6.png)

## 条款3：尽可能使用const

![img](EffectiveC++.assets/E94C2483488D0AB912275FAB853A7357.png)

![img](EffectiveC++.assets/32D50D68CB954ACBD68418F9316E329C.png)

![img](EffectiveC++.assets/974C3348BB41BE9C953E13D93A593B2D.png)

## 条款4：确定对象被使用前已先被初始化

==利用仿真函数，返回一个引用指向定义的一个对象==

![img](EffectiveC++.assets/71BFC61101DB98DB253C62B545079715.png)

![img](EffectiveC++.assets/0A3ED99FD732735FCC16AA90FF6EBE42.png)

![img](EffectiveC++.assets/3C894EEB8DDAE23BD73CE0D874F08FD6.png)

## 条款5：了解C++ 默默编写并调用那些函数

![img](EffectiveC++.assets/DAFC81B2A7ED580BD452B4976B6713E8.png)

## 条款6：若不想使用编译器自动生成的函数，就应该明确拒绝

![img](EffectiveC++.assets/7D9CD76A868B6CA88328E28ED561896A.png)

![img](EffectiveC++.assets/021AF69DAAF51C4EB3E6B54B20CA9E54.png)

## 条款7：为多态基类声明virtual析构函数

![img](EffectiveC++.assets/B91C68A5DF8A2062428C275EE9D3EB29.png)

## 条款8：别让异常逃离析构函数

![img](EffectiveC++.assets/F4876ADB09E708F4510B04FAC9121AD9.png)

## 条款9:决不在构造和析构过程中调用virtual函数

![img](EffectiveC++.assets/62DE1389C61832FC53D53B7A0CD6CCD2.png)

![img](EffectiveC++.assets/8F99CA4E82550591F9EABEEEE243D6FD.png)

## 条款10：令operator= 返回一个reference to *this

![img](EffectiveC++.assets/29B50C6118289655AC1FDC1FE26BDDAE.png)

## 条款11：在operator= 中处理“自我复制”

![img](EffectiveC++.assets/5F6055B97C73202B7AD9D9A7DD075FE8.png)

## 条款12：复制对象时勿忘其每一个成分

![img](EffectiveC++.assets/1BD534C563756B58871B61092F01D992.png)

![img](EffectiveC++.assets/49103CD62FBDFE99B4BF6D308AB1AD86.png)



## 条款13：以对象管理资源

1、把资源放进对象内、便可依赖C++的析构函数自动调用机制，确保资源被释放

其中两个关键想法：

- 获得资源后立刻放进管理对象
- 管理对象运用析构函数后确保资源被释放

![img](EffectiveC++.assets/350C4FF215BE8C79760F75A4D436B3CB.png)

## **条款14：在资源管理类中新校coping行为**

![img](EffectiveC++.assets/B9CA7F77689958A5D485E90EC994EA23.png)

![img](EffectiveC++.assets/089F82DB5D0DE3A09A48EA4968E613B7.png)

![img](EffectiveC++.assets/75585EAC9CB4D4C82BD2439B400B3530.png)

## 条款15：在资源管理类中提供对原始资源的访问

![img](EffectiveC++.assets/6CB113B09262D04F3D21D3430263AC59.png)

## 条款16：成对使用new和delete时要采用相同形式

![img](EffectiveC++.assets/F7442D808A24984580A1571D1778FDF0.png)

## 条款17：以独立语句将newed对象置入智能指针

![img](EffectiveC++.assets/A22A77E3F480945E08F25CC49A5D7CDF.png)

![img](EffectiveC++.assets/E641BD5E2286F74F69023B6D0CADA482.png)

## 条款18：让接口容易被正确使用，不易被误用

![img](EffectiveC++.assets/4E4BF54A9A816B94E4F2235708AA0ED1.png)

## 条款19：设计class犹如设计type

![img](EffectiveC++.assets/66FB12C294F345728B6D96B11FC9F8CF.png)
