---
title: c++面试
toc: true
date: 2018-04-02 14:58:20
tags:
categories: 面试
---



1. 进程与线程有什么区别：

   - 进程是资源分配的基本单位，线程是CPU调度或程序执行的最小单位。在Mac、Windows等采用微内核结构的操作系统中，进程只是资源分配的单位，而不是调度运行的单位，真正调度运行的单位是线程。因此实现并发功能的单位是线程。
   - 进程有独立的地址空间，启动一个新的进程，就需要建立众多的数据表来维护它的代码段、堆栈段、数据段，是一种非常昂贵的多任务工作方式。而运行一个进程中的线程，它们之间共享大部分数据，使用相同的地址空间，因此启动/切换一个线程比进程操作要快，花费要小。但是线程拥有自己的局部变量与堆栈。
   - 线程之间通信比较方便。同一进程下的线程共享数据（比如全部变量、静态变量），通过这些数据来通信方便快捷，但需要处理好访问变量的同步与互斥。而进程之间只能通过进程通信的方式进行。
   - 多进程比多线程健壮，一个线程死掉整个进程就死掉了。但保护模式下，进程死掉对另一个进程没有直接影响。
   - 每个线程都有自己的一个程序入口、顺序执行序列和程序的出口，但线程不能独立执行，必须依附于程序之中，由应用程序提供多个线程的并发控制。

2. 什么是线程安全？

   - 如果多线程的程序运行结果是可预期的，与单线程的运行结果一致，就是线程安全的。

3. 线程的基本概念、线程的基本状态及状态之间的关系？

   - 线程是CPU使用的基本单元；由线程ID、程序计数器、寄存器集合与堆栈组成。与属于同一进程的其他线程共享代码段、数据段与其他操作系统资源（如打开文件和信号）

   - 线程有四种状态：新生状态、可运行状态、被阻塞状态、死亡状态

   - 进程有三种状态：就绪状态、执行状态、阻塞状态

4. 多线程同步和互斥有几种实现方式？

   - 线程间同步方法分为两类：
   - 用户模式：不需要切换内核态，只在用户态完成操作（原子操作、临界区）
   - 内核模式：利用系统内核对象的 单一性同步，使用时需要切换内核态与用户态（事件、信号量、互斥量）

5. 堆和栈的区别：

   一个由C/C++编译的程序占用内存分为以下几个部分：

   - 栈区（Stack）——由编译器自动分配释放，存放函数的参数值，局部变量的值。类似于数据结构中的栈
   - 堆区（Heap）——由程序员分配释放，若程序员不释放，程序结束后由操作系统释放。类似于链表。利用malloc函数或者new运算符
   - 全局区（静态区）（Static）——全局变量和静态变量存储在此，初始化后的全局变量与静态变量在一块区域，未初始化的在相邻的另一块区域。程序结束系统释放
   - 文字常量区——常量字符串。程序结束系统释放
   - 程序代码区——存放函数体的二进制代码

   ```c++
   //main.cpp 
   int a = 0;  // 全局初始化区 
   char *p1;   // 全局未初始化区 
   main() 
   { 
   int b; 		// 栈 
   char s[] = "abc"; // 栈 
   char *p2;   // 栈 
   char *p3 = "123456"; // 123456\0在常量区，p3在栈上。 
   static int c =0； // 全局（静态）初始化区 
   p1 = (char *)malloc(10); 
   p2 = (char *)malloc(20); 
   // 分配得来得10和20字节的区域就在堆区, p1,p2本身在栈上。 
   strcpy(p1, "123456"); // 123456\0放在常量区，编译器可能会将它与p3所指向的"123456"优化成一个地方。 
   } 
   ```

6. fork()函数

   - fork函数会返回两次结果，因为操作系统会把当前进程的数据复制一遍，然后程序就分为两个进程继续运行后面的代码，fork分别在父进程和子进程中返回。子进程中返回的值pid为0，父进程返回的是子进程id

7. ​