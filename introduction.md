
# 学习 bash 笔记

## 前言

我这次学习 bash 是有目的的。

因为我要写一个小脚本，实现快速登录 ssh.

ssh 命令很简单，但是我们的需要登录的ssh 比较多时，再简单的命令不断操作起来也会变得繁琐。

所以我想通过运行一个脚本快速的使用 ssh 登录远程桌面。

当然，我已经把我的ssh密钥传到所有的要登录的服务器上了。

注:我通过阅读 《bash 笔记》 简单的实现了这个脚本，然后记录下 bash 的基本操作，以做记录。

## 编写 bash 的工具

使用编辑器编写即可，我一般使用 vi 编写。

## 运行 bash

假设要运行的bash文件是file.sh, 使用命令 sh file.sh 或 ./file.sh 即可。

在 file.sh 后名可以跟参数，参数使用空格或TAB隔开。

## bash 介绍 

一个 bash 文件，就是包含 shell 命令的文件，也是一个 shell 程序。

### shell 变量

变量用来暂时储存数据。

使用 varname=value 来给变量赋值。等号两边不能有空格。

使用 ${varname} 可以获得变量的值。大括号可以省略。


### 有类型变量

使用 declare 加下面的参数声明特定的变量。

* -a 将变量看作数组 
* -f 只使用函数名
* -F 显示未定义的函数名
* -i 将变量看作整数
* -r 使变量只读
* -x 标记变量未通过环境导出

### 位置参数

位置参数可以理解为函数的参数。一个bash 文件也可以理解为一个函数。

位置参数使用 $0,$1,$2 等获得他们的值。

$\* 代表包含所有参数位置的单一字符串。
$@ 等价与 N个单独的由空格分隔的双引号字符串。

### 函数

函数可以理解为一个独立的程序块，可以多次使用。


### 字符串与模式

关于字符串的操作，具体参考 [这里](<base.md>)


### 条件测试

shell 使用\[] 结构提供了测试各种条件的方式,称为test测试。

可以使用该结构检验一个文件的各种属性(是否存在，文件类型，权限和所有者)，或比较两个文件那个更新，以及对字符串进行比较。

[ 和 ] 的后和前必须有空格。


#### 字符串比较

* == 匹配
* != 不匹配
* < 小于
* \> 大于
* -n str 为null,长度大于0
* -z str 为null,长度为0

分号是 shell 的标准语句分隔字符。


#### 文件属性检查

* -d file file存在并且为一个目录
* -e file file存在
* -f file file存在并且为一个正规文件
* -r file 对 file 有读权限
* -s file 文件存在且非空
* -w file 对 file 有写权限
* -x file 对file有可执行权限，如果为目录，则有目录搜索权限
* -O file 你是file的所有者
* -G file file的组ID匹配你的ID
* file1 -nt file2 file1比file2新
* file1 -ot file2 file1比file2旧

-a 和 -o 操作符类似于退出状态时所用的 && 和 ｜｜ 操作符。只有在test条件表达式内可用。

#### 整数条件

* -lt 小于
* -le 小于等于
* -eq 等于
* -ge 大于等于
* -gt 大于
* -ne 不等于



### if 流程

````
if condition
then
    statements
elif
    statement
else
    statements
fi
````

### for 流程

````
for name \[in list]
do
    statement
done
````

### 其他流程

其他流程有 case, select, while, until等，不多介绍。


### 其他需要用到的东西

read 可以读入一个字符串。



