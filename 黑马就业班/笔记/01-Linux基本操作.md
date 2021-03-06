

大多数后台程序运行在Linux操作系统上的

# 一、基础知识

## 1.1 操作系统（了解）

**控制硬件** 为**用户提供软件服务**的 **系统程序**

虚拟机软件：虚拟出一套计算机硬件 给 虚拟机系统使用

![](D:\黑马python就业班\day01-Linux 基本操作\老师\02-其他资源\01-虚拟机原理.png)



## 1.2 Linux系统（了解）

UNIX 系统 —> MINIX —> LINUX —> MAC

这些都是类 UNIX 操作系统

内核版本：

​	只提供非常基础的功能  用户不能直接使用的

Linux发行版（内核 + 包装界面 工具 软件）：

​	ubuntu

​	centos/redhat

​	深度 红旗

查看发行版中内核版本：

> python@ubuntu:~$ uname -a
> Linux ubuntu 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux



## 1.3 windows 对比Linux（理解）

windows 有多个根目录  一个分区就是一个根目录

Linux 系统只有一个根目录 / 

​	/  系统根目录

​	/home  存储所有用户家目录的目录

​	/home/xx/  xx 用户的家目录/主目录  root  用户家目录

在/root/  超级管理员用户

![](D:\黑马python就业班\day01-Linux 基本操作\老师\02-其他资源\02-win 与 Linux 区别.png)



# 二、Linux命令

## 2.1 终端基本操作（ls、tree重点，其余了解）

```
简单明了预览：
ls  查看目录下的信息（一层） **

tree  查看文件目录结构（多层）--树状图 **

cd  切换当前路径		'cd 目录名'

清屏	clear	'ctrl l'

放大	'ctrl +	===	ctrl shift ='

缩小	'ctrl -'

pwd  查看当前路径
```



## 2.2 cd命令 **

```shell
cd /home/xxx  回到用户主目录 === cd ~  当前用户主目录 === cd

cd ..  返回上一级路径

# 下面命令了解
cd .  当前路径
cd -  返回上一次命令所在的路径
```



### 2.2.1 相对路径 

​	从当前路径 . 出发的路径	./ 一般可以省略

### 2.2.2 绝对路径 

​	从根目录 / 出发的路径



## 2.3 touch命令（理解）

touch 文件名

- 如果文件不存在，则创建一个空文件
- 扩展 -- 如果文件存在，修改文件时间为当前时间，内容不变



cat 文件名称

- 查看文件内容

> Tab  自动补齐文件名/目录名



## 2.4 mkdir 创建目录 **

```shell
命令  选项  参数
单层目录：
	mkdir 目录名
多层目录：
	mkdir -p 2/3/4
​ 命令表示	做什么
​ 参数表示	对谁做
​ 选项表示	怎么做
```

 创建目录：mkdir 目录名称 

- Linux在创建多级目录时，要求其父目录也存在；如果父目录不存在则操作失败
- -p 意义就是在创建目录时，自动创建所需的父目录

![](D:\黑马python就业班\day01-Linux 基本操作\老师\02-其他资源\03-创建目录.png)

![04-创建目录的选项](D:\黑马python就业班\day01-Linux 基本操作\老师\02-其他资源\04-创建目录的选项.png)



## 2.5 删除文件或目录（理解）

rm -r 目录名称  删除目录

> rmdir  删除空目录  了解



移动文件、移动目录 move

​	mv 源路径/名称  目的路径

​	mv ./hehe py23



## 2.6 ls命令选项详解 **

作用：查看 目录的内容contents(文件  目录信息)

格式：ls  选项  路径

​	路径默认为当前路径

> 查看用户主目录下的文件：ls ~

选项说明：

- -l  列表方式显示详细信息，权限、大小、文件名。。。
- -h 以人类友好的方式显示文件大小，human begin，==一定要和-l 合用==
- -a 显示所有文件（开始的文件或者目录 默认不显示 - 隐藏文件）

![](D:\黑马python就业班\day01-Linux 基本操作\老师\02-其他资源\05-文件详细信息说明.png)



## 2.7 rm命令 **

作用：删除 文件或者目录

格式：rm 选项 文件名1 2 3 4

选项：

- -r 递归删除  一般在删除目录时使用  删除文件也可
- -f 强制删除（忽略不存在的错误提示）
- -i 交互 需要用户确认
- -d 删除空目录(了解)

> 慎用！！！
>
> rm -rf /：递归强制删除主目录下的所有文件



## 2.8 复制cp 命令 **

作用：复制(copy –> cp)文件或者目录

格式：cp 选项 源路径/名称 目的路径/

​	cp 源路径/名称 目的路径/

​	cp ./hehe py23/

复制目录：

​	cp -r 源路径/源目录名称 目的路径

选项：

- ** -r 递归拷贝目录 
- ** -i 交互 - 如果文件存在需要用户确认是否覆盖；文件不存在则无作用
- -v 显示复制的文件的路径信息
- -a 在复制文件时保留文件原有属性（权限、时间…）



## 2.9 移动、重命名文件 mv 命令 **

作用：

- 移动文件
- 重命名文件

格式：

​	移动：mv 源路径/名称 目的路径/

​	改名：mv 原有名称 新名称

​	移动文件并且改名：mv 原有路径/原名称 目的名称/新名称

选项（与cp 命令选项一致）：

- -i 交互 -- 如果文件存在需要用户确认是否覆盖；文件不存在则无作用
- -v 显示移动的文件的路径信息



## 2.10 终端命令格式--命令帮助信息（了解）

### 2.10.1 命令名 选项 参数

- 选项和参数可以有0个、1个或者多个

### 2.10.2 查看命令帮助

- --help 使用说明：命令名 --help
- man（离线手册） 使用说明：man 命令名
  - 空格：显示下一屏信息
  - f：显示下一屏信息
  - b：显示上一屏信息
  - 回车：显示下一行信息
  - q：退出

# 三、表格

| 命令                            | 选项                                                         | 文件                    | 目录                       |
| ------------------------------- | ------------------------------------------------------------ | ----------------------- | -------------------------- |
| 基本操作                        |                                                              |                         |                            |
| uname -a  查看内核版本          |                                                              |                         |                            |
| ls 查看目录下的信息（3种）      | -l 列表方式显示详细信息  权限 大小 文件名...                 |                         |                            |
|                                 | -h 以人类友好的方式显示文件大小 human begin  一定要和-l 合用 |                         |                            |
|                                 | -a  显示所有文件(.开始的文件或者目录 默认不显示 - 隐藏文件)  |                         |                            |
| tree 查看文件目录结构 -- 树状图 |                                                              |                         |                            |
| cd 切换当前路径（5种）          | cd /home/xxx  回到用户主目录                                 |                         |                            |
|                                 | cd ~  当前用户主目录                                         |                         |                            |
|                                 | cd ..  返回上一级路径                                        |                         |                            |
|                                 | cd .   当前路径                                              |                         |                            |
|                                 | cd -  返回上一次命令所在的路径                               |                         |                            |
| pwd 查看当前路径                |                                                              |                         |                            |
| ctrl l 清屏                     |                                                              |                         |                            |
| 创建                            |                                                              | touch                   | mkdir -p 2/3/4             |
| 查看内容                        |                                                              | cat                     |                            |
| 复制 cp（4种）                  | -r 递归拷贝目录                                              | cp 源路径/名称 目的路径 | cp -r 源路径/名称 目的路径 |
|                                 | -i 交互 - 如果文件存在需要用户确认是否覆盖; 文件不存在则无作用 |                         |                            |
|                                 | -v 显示复制的文件的路径信息                                  |                         |                            |
|                                 | -a 在复制文件时保留文件原有属性(权限 时间...)                |                         |                            |
| 移动 mv（2种）                  | -i  交互-如果文件存在需要用户确认是否覆盖; 文件不存在则无作用 | mv 源路径/名称 目的路径 | mv 源路径/名称 目的路径    |
|                                 | -v  显示移动的文件的路径信息                                 |                         |                            |
| 删除 rm（4种）                  | -r 递归删除  一般在删除目录时使用 删除文件也可               | rm                      | rm -r                      |
|                                 | -f 强制删除(忽略不存在的错误提示)                            |                         |                            |
|                                 | -i 交互 需要用户确认                                         |                         |                            |
|                                 | -d 删除空目录                                                |                         |                            |

总结：

- 文件的创建与目录的创建不一样
- 复制、删除：目录需要加 -r（递归），
- 移动：文件和目录的方式一样
- 复制、删除、移动：都有交互 -i
- ==关于命令操作都是重点==