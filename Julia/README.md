<a name="logo"/>
<div align="center">
<a href="https://julialang.org/" target="_blank">
<img src="https://julialang.org/images/logo_hires.png" alt="Julia Logo" width="210" height="142"></img>
</a>
</div>

# Julia Documentation 1.0
## Julia  安装 （统一安装JuliaPro）
为便于在Jupyter notebook中使用Julia, 需要安装IJulia
- **Windows** 打开JuliaPro界面以后，   ']'进入package模式后输入：

```
pkg> add IJulia 
```
等待的过程中会穿线验证界面，用github账户直接注册验证即可，安装时间与网速有关，安装完成后，出现：
```
Building Conda 
Building ZMQ
Building IJulia
```
通过的界面，然后在REPL端口直接输入：
```
notebook()
```
即可在Julia内核下面开启Julia

---

- **Mac** 为防止在使用REPL的过程中出现无法解决的 *permission denied* 的 **System error** 

在打开 JuliaPro之前，由于 Mac自身的系统保护做的太好了😂，需要给/Users/Name目录下面的.Julia隐藏文件授予读写的程序的读写权利：

```
$ sudo chown -R Name:staff .julia
```
然后找到/Applications文件夹下面的JuliaPro的图标，给这个文件授予文件读写的权利： 
```
$ sudo chown -R Name:staff /JuliaPro-1.0.1.1.app
```
在这两步完成后，按照Windows下相同的操作，即可设置正确的Jupyter内核。

## Julia 安装完成后
- Julia在安装完成后，可能会直接影响到原来Anaconda的安装内核（**都是用conda统一管理包环境**），直接结果就是GUI版本的Anaconda Navigator无法直接打开，Terminal环境下可以运行相关 **conda -h**命令；
---
- 解决办法：在终端使用一系列命令：
 ```
 $ conda update anaconda-navigator
 $ anaconda-navigator --reset
 $ conda update anaconda-client
 $ conda update -f anaconda-client
 
 ```
  完成后，执行命令：
```
$ conda info --env
```
可以看到 **conda** 管理的环境下出现了Julia的package list

- 由于VScode中的插件Julia暂时不支持1.0的版本，所以为了语法补全建议使用ATOM+Juno的Julia编译环境，另外不建议使用下面的命令在REPL下打开notebook()环境，不经超慢，而且不稳定，建议使用系统自带的Jupyter打开：

```
$ using IJulia
$ notebook()

$ jupyter notebook #支持Julia内核
```
## Numerical Literal Coefficients
可以用来写简单的多项式的表达式（不建议用在复杂的表达式上-混淆函数的调用方式）
```(julia)
$ julia> x =3
$ julia> x^2 -3x + 1
$ julia> 1
```
---
## Vectorized "dot" operator（Dot Syntax for Vectorized Functions）
- Any Julia function **f** can be applied elementwise to any array(or other collection) with the syntax **f.(A)** 

- 直接在原来的内存结构上进行单次的循环操作，并创建一个暂存的维数相同的内存结构

```(julia)
 > f.(args...) --- broadcast(f, args...) # f既可以是函数也可以是算符
 > X.= ... --- broadcast!(identity,X,...)
 > @. expression --- broadcast form
 > a .+= b --- a .= a .+b
 > X.(四则运算)
```
- 可使用在**user-defined operators**

---
## Complex Numbers
- Global constant **im** is bound to represent complex number **i**

```(julia)
> sqrt(-1 + 0im)
> complex(a,b) --- a + bim
``` 
---

## String
- 字符串的查找从**1**开始
- Julia中的取值运算符**$**同***Linux*相同，可以作用在字符串或者表达式中
- findfirst等函数找到第一个是**True**的值的***index**


```(julia)
> str = "Hello World"
> str[1] --- 'H'
> "Hello " * "World" --- "Hello World" 
> $str --- "Hello World"
> findfirst(predicate::Function, A)
> findfirst(isequal('o'),"xylophone") --- 4
```
> '**+**' operator usually mean the operator is commutable for objects 

---
## Regular Expressions(正则表达式)
- Find regular patterns in strings
- Act as an input to help search effectively

### 正则表达式简介（回顾以后）
用来查找符合某些规则的字符串的需要所使用的描述这些规则的工具

---
## Functions
```(julia)
> function f(x,y)::Int8 #给定返回值的类型
    x+y
end             # traditional syntax
> f(x,y) = x +y # assignment form
> function hypot(x,y)       #使用语句块的方法可以使代码readable,不想Python强制
    x = abs(x)
    y = abs(y)
    if x > y
        r = y/x
        return x*sqrt(1+r*x) 
    end
    if y == 0
        return zero(x)
    end
    r =x/y
    return y*sqrt(1+r*x)
 end                        #每一个地方的语句块的结束必须有 end
```
- **"pass-by-sharing"** :只是为传递的参数建立了一个新的引用，如果函数参数是可变对象，在函数调用过程中可能会直接改变函数参数

- The value returned by a function is the value of the last expression evaluated.(如果在函数定义中显式地申明了**return**，则返回**return**后面的语句，且作为结束的标志) 
### Anonymous Functions
- passing them to functions which take other functions as arguments

```(julia)
$ map(x -> x^2 + 2x - 1, [1,3,-1])
```
> 1. Julia中可迭代对象类同于Python中的元组，列表，字典；
> 2. Julia中的自动Destructing Argument(可以通过传递可变的参数给一个函数)

```(julia)
bar(a,b,x...) = (a,b,x)

map(x->begin                #  整体作为map的应用函数
           if x < 0 && iseven(x)
               return 0
           elseif x == 0
               return 1
           else
               return x
           end
       end,
    [A, B, C])

map([A, B, C]) do x         # reserved key-word do使用
    if x < 0 && iseven(x)
        return 0
    elseif x == 0
        return 1
    else
        return x
    end
end
```
#### Do-Block Syntax for Function Arguments（回顾）
---

---
## Control Flow
### Compound Expressions
- Evaluates several subexpressions in order, returning the value of the last subexpression as its value(可以连续执行多条命令，最后返回最后一个)

```(julia)
> z = begin             # 缩进不是默认要求
           x = 1
           y = 2
           x + y
       end

> z = (x = 1; y = 2; x + y) # 也可以缩进
```
---
## Conditional Evaluation
- if-elseif-else判断结构，而且最后会默认返回判断语句最后的表达式

- 只有**True False**在Julia结构中可以实现判断

```(julia)
> function test(x,y)
           if x < y
               relation = "less than"
           elseif x == y
               relation = "equal to"
           else
               relation = "greater than"
           end
           println("x is ", relation, " y.")
       end

> test(x, y) = println(x < y ? "x is less than y":x > y ? "x is greater than y" : "x is equal to y") # 直接进行short expression语法的判断
```
---
