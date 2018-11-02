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
