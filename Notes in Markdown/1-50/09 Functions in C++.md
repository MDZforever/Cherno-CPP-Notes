## 1. Definition

避免代码重复等问题，执行特定任务

```cpp
    int Multiply(int a,int b)
     |
 return type(void 则不返回)
	{
		return a * b;
	}
```

^131a42


## 2. 调用原理

#### 假设编译器决定保留我们的函数作为一个函数而非*inline*(内联):

我们每次调用函数时，编译器生成一个[调用指令](06%20How%20the%20C++%20Compiler%20Works.md#^d63649)，我们需要为这个函数创建一整个*stack frame*(栈框架),也就是说要把**参数**等东西和**返回地址**==push==到栈上。

流程就是跳到程序的某个不同部分，执行我们函数中的命令，然后将push的返回值返回给调用函数之前的位置。需要占用时间，减慢了程序，因此不需要每一行都设个函数。

## 3. 返回值

定义了返回值则[必须返回](05%20How%20C++%20Works.md#^d4cfc1)，除非是`main`函数，它默认return 0 

不过报错仅限于`Debug`模式，当特定的*flags*(调试编译标记)被激活时，会给我们报错来帮助调试代码

如果改成`Release`模式，则编译不会报错，但是如果调用会得到*undefined behavior*

