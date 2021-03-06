# C++学习笔记1 - C到C++的升级

[TOC]

## C与C++的关系

* C++继承了所有的C特性
* C++在C的基础上提供了更多的语法和特性
* C++的设计目标是运行效率与开发效率的统一
* 特点:
    * 以C语言为基础
    * 面向对象支持
    * 类型加强、函数加强、异常处理等

## C++对C的加强

1. C++语言中所有变量都可以在使用时定义, C语言中的变量必须在作用域开始的位置定义(**C99标准已经支持新特性**)
2. register关键字的变化
    * C语言中register关键字请求将变量存储在寄存器中(但不一定成功), 并且无法取得register变量地址
    * C++语言不使用register也会主动优化, **支持register关键字仅为了兼容C语言**
3. 同名全局变量的定义
    * 在C语言中, 重复定义多个同名的全局变量是合法的
    * 在C++中, 不允许定义多个同名的全局变量
4. C++编译器对const常量的处理
    * 当碰见常量声明时, 在符号表中放入常量的值
    * 编译过程中若发现使用常量则**直接以符号表中的值替换**
    * 编译过程中若发现对const使用了extern或者&操作符, 则给对应的常量分配存储空间
    * 注意: C++编译器虽然可能为const常量分配空间, 但**不会使用其存储空间中的值**
    * C语言中const变量仅仅是只读变量, 有自己的存储空间
    * C++中的const常量, 下列情况分配存储空间
        * 当const常量为全局, 并且在其它源文件中使用
        * 当使用&操作符取const常量的地址
    * C++中的const常量类似于宏定义
    * C++中的const常量与宏定义不同
        * const常量由编译器处理, 提供类型检查和作用域检查
        * 宏定义由预处理器处理, 是单纯的文本替换
5. struct类型的加强
    * C语言的struct定义了一组变量的集合, C编译器并不认为这是一种新的类型
    * C++中的struct是一个新类型的定义声明
    * 例如, 定义类型`struct Student {const char *name, int age};`
        * C语言中, `struct Student s1;`定义struct变量
        * 在C++中, `Student s1;`直接定义变量
6. 类型加强
    * C++中所有的变量和函数都必须有类型
    * C语言中的默认类型在C++中是不合法的
    * `int f();`与`int f(void);`的区别
        * C语言中, `int f();`表示接收任意参数的函数, `int f(void);`表示无参数函数
        * 在C++中, `int f();`与`int f(void);`都表示无参数的函数

## 小结
* C++更强调实用性, 可以在任意的地方声明变量
* C++的register只是一个向后兼容的作用, C++编译器能够进行更好的变量优化
* C++中的const是一个真正意义上的常量, 而不是只读变量
* C++更加强调类型, 任意的程序元素都必须显式指明类型
