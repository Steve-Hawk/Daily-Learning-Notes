# Mac中VIM配置方法
## Bug
- MacOS系统升级的过程中，可能会直接影响macports安装软件使用port的版本，同时需要直接升级Xcode的版本，安装新版本的command-line tool 

> [macports](https://trac.macports.org/wiki/Migration)(重新安装macport)

-------------

- Mac系统中自带的VIM本身并不完整，通常比最新版本的VIM版本低，而且自带的VIM编译环境并不完整，建议使用github上的源码安装的方法:

```
$ git clone https://github.com/vim/vim.git
$ cd vim
$ ./configure --with-features=huge --enable-pythoninterp --with-python-config-dir=/path/to/python2 --enable-rubyinterp --enable-luainterp --enable-perlinterp --enable-multibyte --enable-cscope --prefix=/path/to/vim/
$ sudo make install
```

> 这里由于VIM动态加载编译时添加的python选项，如果编译时选择了两种版本的python环境，则后续的VIM识别的过程中不会识别任何一种python版本,查看是否支持python的后续编译,直接影响到YoucompleteMe插件的安装过程

> 上面介绍的方法在MacOS系统下的操作比较方便，貌似是由于不涉及Python-devel的原因，在Linux系统下，需要安装必要的python-devel的文件（Anaconda不支持头文件），VIM的安装过程中会寻找依赖的头文件(貌似在MacOS系统下也会有一定的问题)


- 比较快捷的方法：

```(shell)
$ alias python=python3
$ brew install vim
$ unaliase python
```
> 上述步骤完成之后，需要重新编译安装YoucompleteM



```
$ vim --version|grep python
```
---
**查找python安装路径-替换上面的路径，只能选择一种Python**
```
$ which python
$ whihc python3
```
---
**添加安装的VIM到用户环境变量中-终端启动时使用新安装的VIM**
```
$ export PATH="\$PATH:/path/to/vim/bin:$PATH"
```
- 系统VIM与用户安装的VIM同时使用/.vimrc中的配置文件

---
**查看终端VIM加载程序顺序**
```
$ vim
$ :scriptname
```
---
**安装后续插件的过程建议通过Vundle插件管理**
- 在使用YouCompleteMe的使用需要转到相应的bundle文件夹下面，用编译时选择的python选项，运行

```(shell)
python install.py
```
---
