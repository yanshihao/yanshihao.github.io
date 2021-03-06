### 深度探索C++对象模型

学习《深度探索C++对象模型》让我更加深入的了解了C++语言到汇编语言的转换过程，知其然且知其所以然。同时也对C++的对象、函数、模板、运行时类型识别有了更加深刻的理解。

如果撇开多重继承和虚拟继承，其实整个模型也不太复杂。



1. 函数

   函数的参数传递是通过结合寄存器以及函数栈来实现的，当传递指针或者引用的时候往往采用寄存器，而传递一个较大的对象的时候可能就会采用函数栈的形式来传递。同时，也有可能把返回值的地址传入进去，这样可以减少拷贝构造的次数。

2. 访问权限

   对于汇编语言，倒是不存在C++里面的访问权限。因此，访问权限相当于一个属于C++的抽象层。编译器会告诉我们哪些函数不合法，然后报错，属于C++语法层面的问题。

3. 抽象数据类型函数的运行效率和普通函数相当

   类内的函数调用可以转换为对 this 指针进行操作

4. 无虚函数的继承一般情况下不影响效率

   然而内存对齐会使得类因为填充而变得更加庞大，同时无虚函数的单继承之前指针也不需要增加偏移量

5. 存在虚函数的继承，在指针访问情况下会多一层间接性

   虚指针和虚表，因此在构造、析构、拷贝、赋值等函数中需要对虚指针进行操作。同时指针访问成员函数也需要通过虚指针加上偏移量才能访问函数。这个偏移量在编译器就确定了，但是虚指针的指向是不确定的，视指针实际指向的对象定。

6. 
