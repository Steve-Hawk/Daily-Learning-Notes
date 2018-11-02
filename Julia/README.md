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
