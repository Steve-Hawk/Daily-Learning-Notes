# Learning Linux The Hard Way

## Cat
- MAN 文档描述：
```(shell)
NAME
       cat - concatenate files and print on the standard output

SYNOPSIS
       cat [OPTION]... [FILE]...

DESCRIPTION
       Concatenate FILE(s), or standard input, to standard output
with no FILE, or when FILE is -, read standard input to standard output
```
实际使用过程中，```cat``` 返回参数文件的内容到标准输出

> Linux任何东西都是文件，包括标准输入以及标准输出(stdout stdin),默认标准输入是键盘，标准输出是显示屏幕

```(shell)
$ cat -
1234
1234 # 这是返回显示的内容
5678 
5678 # 返回显示的内容
Ctrl+C #退出输入
```
```(shell)
$ cat <<EOF > new.txt
> 1234
> 5678
> EOF # 本来是需要显示到屏幕上
$ cat new.txt
1234
5678
```
这里 ```<<EOF```是一种 ```Tag Document```，可以处理成为一种**临时文件**来理解，其中输入的终止提示符可以换成任意的标记，文本输入以此作为输入的结束
