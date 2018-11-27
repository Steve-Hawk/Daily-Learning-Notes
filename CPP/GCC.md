# GCC编译参数

- 源代码文件
```(c++)
// Hello.cpp
#include<iostream>

int main()
{
    std::cout << "Hello World" << std::end;
    return 0;
}
```
---
## CPP编译成可执行文件过程
    1. Pre-processing（生成```.i```文件）
    2. Compilation（将预处理后的文件转换为汇编语言）
    3. Assembly（将汇编转变为目标代码/机器代码）
    4. Linking（连接目标代码，生成可执行程序）

```(shell)
$ gcc -Wall Hello.cpp -o Hello
```
### 解释
    1. gcc - 调用GNU编译器
    2. -Wall - gcc flag that enables all warnings: -W stands for warning, and we are passing "all" to -W
    3. Hello.cpp - Input Cpp Program
    4. -o Hello - Instruct GNU compiler to create Cpp executable as Hello. (用来自定义可执行文件的名称)
---

### Pre-Precessing
- 编译器任务：
    1. Macro substitution
    2. Comments are striped off
    3. Expansion of the inclueded file

### 解释
- Using flag -E: print the preprocessed output to stdout
```(shell)
$ gcc -Wall -E Hello.cpp
```
- Using flag -save-temps : Instruct complier to store the tempory intermediate files used bu the GCC complier in the current directory
```(shell)
$ gcc -Wall -save-temps Hello.cpp -o Hello
```
---
### Compiling
- 生成汇编语言层面上的指令代码
---
### Assembly

利用在第二阶段生成的```Hello.s```文件作为输入生成```Hello.o```对象文件（其中```.o```类型的文件包含机器曾层面上的指令）

---
### Linking
- 找到相应函数定义位置
- 添加一些必要的函数代码
最终将```.o```文件转化为可执行文件

### 总结
在用GCC编译大型的程序时，通常使用Makefile编写编译命令，而且在GCC的编译选项中通常需要指定库文件的目录位置

---