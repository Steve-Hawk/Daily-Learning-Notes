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
