<a name="logo"/>
<div align="center">
<a href="https://julialang.org/" target="_blank">
<img src="https://julialang.org/images/logo_hires.png" alt="Julia Logo" width="210" height="142"></img>
</a>
</div>

# Julia Bug(Solutions)
## 安装Julia Pro版本：
### pkg问题
#### 只能在终端安装少数Package
- 删除掉Julia安装文件夹下registry文件夹（可能是集成环境Julia Pro的问题，只预先存储了少部分的Package Library的记录）
- 找到需要安装的Package的GitHub的地址，在终端输入```add URL```
- 命令执行完后，pkg的文件夹下会出现关于registry的general文件夹（基本包含了Package Library下的所有Package）

```(julia)
> add "package name"
```
