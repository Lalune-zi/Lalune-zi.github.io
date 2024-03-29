---
title: RHCSA学习
date: 2023-08-14 20:21:49
updated:
tags: RHCSA学习
categories: RHCSA学习
---

本篇博客为RHCSA学习过程中的学习笔记，如有错误，感谢指出。CSDN同步更新。
<!-- more -->


# 1 第一天
## 1.1 终端介绍

`[root@localhost ~]#`

其中 “root”代表当前终端使用用户，localhost代表主机名，是IP地址的映射。
相关命令以及部分快捷键：
| 功能 |  命令     |
|:--------:| :-------:|
| 查看完整主机名 | `hostname` |
| 修改主机名 | hostnamectl set-hostname 主机名 |
| 放大终端 | ctrl  + shift +  “=” |
| 缩小终端 | ctrl    +  “-” |
| 清屏 | ctrl  + “l”（小写的L）|
| 终止当前程序 | ctrl + “c” |
| 补全命令 | tab |
| 调用之前使用过的命令 | 方向上下键 |
| 复制 | Ctrl+shift+“c” |
| 粘贴 | Ctrl+shift+“d” |
| 历史命令（默认保留一千条） | history |
| 调用历史命令 | ！ + 命令编号 |

## 1.2 命令组成
命令由三部分组成：
1. 主命令：代表要操作的行为
2. 选项：通常是带“-”或者带“--”的字符，表示对主命令的补充
3. 参数：操作行为的对象
这三者之间使用空格隔开

## 1.3帮助命令
在使用命令时，可能会不清楚某操作的具体选项，这时可以使用帮助命令进行查找，有两种方式：
命令    |  功能
-------- | -----
主命令 + `--help`  | 在终端屏幕上输出该主命令的简洁帮助信息
`man` + 主命令  | 打开man手册，man手册会在终端上打开，但是并不会在终端屏幕上输出，退出man手册后并不会在终端上残留信息

在man手册中查找例子，只需要在查看man手册时，输入`/EXAMPLE`之后回车，如果由例子便会自动跳到例子处，退出man手册只需要按q即可

## 1.4 主命令：ls
ls是一个常用命令，用于列出当前目录中的文件和子目录。它的名称是 “list” 的简写。
它的基本语法为：


```bash
ls [选项] [文件或目录]
```

 下面是一些常见的命令选项：
 选项     | 功能
-------- | -----
 -l|以长格式（详细信息）显示文件和目录的列表。
-a|显示所有文件和目录，包括以点（.）开头的隐藏文件。
-h|使用人类可读的格式（例如，KB、MB 等）显示文件大小。
-d|目录本身
-t|按修改时间排序，并显示最新的文件或目录。

## 1.5 主命令：cd
cd 是一个常用的命令，用于更改当前工作目录，它的名称是 “Change Directory” 的简写。
它的基本语法为：


```bash
cd [目录路径]
```

常用命令：
命令    | 功能
-------- | -----
cd  | 切换当前用户的主目录
cd + 绝对路径  | 切换至绝对路径对应的目录
cd + 相对路径  | 切换至相对路径对应的目录
cd . | 返回当前目录（类似刷新）
cd . . | 返回上一级目录
cd - |返回上一个目录

## 1.6 主命令：mkdir
mkdir 是一个常用的命令，用于创建新的目录（即文件夹）。它的名称是 “Make Directory” 的简写。

它的基本语法为：


```bash
mkdir [选项] 目录名
```

1.[选项] 是可选的参数，用于指定命令的一些特殊行为。
2.目录名 是要创建的目录的名称。
3.如果不加选项，该命令仅能在当前目录下创建新的目录。

常用命令选项：
选项    | 功能
-------- | -----
-p|递归创建目录。如果指定的目录路径中的某些父目录不存在，会自动创建这些父目录。
-m|指定目录权限。可以通过权限值（如 755）或符号形式（如 rwxr-xr-x）来设置目录的权限。

## 1.7 主命令：touch
touch 是一个常用的命令，用于创建新的空文件或更改现有文件的访问和修改时间。它的名称代表了 “Touch” （触摸）文件的意思。

它的基本语法是：


```bash
touch [选项] 文件名
```

1.[选项] 是可选的参数，用于指定命令的一些特殊行为。
2.文件名 是要创建或修改的文件的名称。
使用 touch 命令时，可以指定一个现有文件的名称，以更新该文件的访问和修改时间。如果指定的文件不存在，touch 命令将创建一个新的空文件。

常用选项：
选项     | 功能
-------- | -----
-c|仅当指定的文件不存在时，才创建新文件。
-t|使用指定的时间戳（格式为 [[CC]YY]MMDDhhmm[.ss]）来设置文件的访问和修改时间。

## 1.8 主命令：rm
rm 是一个常用的命令，用于删除文件或目录。它的名称是 “Remove” 的简写。

它的基本语法如下：


```bash
rm [选项] 文件/目录
```

1.[选项] 是可选的参数，用于指定命令的一些特殊行为。 
2.文件/目录 是要删除的文件或目录的名称。

常用选项：
选项    | 功能
-------- | -----
-f|强制删除
-d|删除空目录
-r/-R|递归删除一个非空目录
-i|交互式删除，删除之前提示用户确认操作。
-v|详细模式，显示每个删除的文件的名称。

**绝对不可以使用的命令：**
`rm -rf /*`
==此命令会删除磁盘中的所有东西！==
## 1.9 主命令：mv
mv 是一个常用的命令，用于移动文件或重命名文件。它的名称是 “Move” 的简写。

它的基本语法如下：


```bash
mv [选项] 源文件/目录 目标文件/目录
```

1.[选项] 是可选的参数，用于指定命令的一些特殊行为。 
2.源文件/目录 是要移动或重命名的文件或目录的名称。 
3.目标文件/目录 是要移动到的目标位置的名称。

如果要重命名一个文件，可以将该文件作为源文件参数，并指定新的文件名作为目标文件参数。

常用选项：
选项     | 含义
-------- | -----
-i|交互式操作，即在执行操作之前提示用户确认操作。
-f|强制执行操作，即不提示确认并覆盖同名文件。
-v|显示详细操作，即显示每个移动或重命名的文件的名称。

## 1.10 主命令：cp
cp 是一个常用的命令，用于复制文件和目录。它的名称是 “Copy” 的简写。

它的的基本语法如下：


```bash
cp [选项] 源文件/目录 目标文件/目录
```

1. [选项] 是可选的参数，用于指定命令的一些特殊行为。 
2. 源文件/目录 是要复制的文件或目录的名称。 
3. 目标文件/目录 是要将源文件/目录复制到的目标位置的名称。

常用选项：
选项     | 含义
-------- | -----
-r 或 --recursive| 递归复制目录及其内容
-i 或 --interactive  |交互式复制，如果目标文件已存在，会提示是否覆盖
-u 或 --update  | 只复制比目标文件新或目标文件不存在的文件。
-v 或 --verbose | 显示详细的复制过程
-f或--force | 强制复制文件并覆盖已存在的目标文件
# 2 第二天

## 2.1 主命令：tar
tar是一个在Linux系统中常用的用于打包和压缩文件的命令。它常用于创建备份、制作软件包以及在不同系统之间传输文件。

tar命令的基本语法如下：

```bash
tar [选项] [文件/目录...]
```

常用选项：
选项    | 含义
-------- | -----
-c|创建新的归档文件（或称为tar包）。
-x|从归档文件中提取（解压）文件。
-f|指定归档文件的名称。
-v|显示详细输出，列出被处理的文件。
-z|使用gzip进行压缩或解压缩。
-j|使用bzip2进行压缩或解压缩。
-C|指定文件或目录的路径。

一些例子：
创建一个新的归档文件：

```bash
tar -cvf archive.tar file1.txt file2.txt
```
解压缩归档文件：

```bash
tar -xvf archive.tar
```

使用gzip压缩归档文件：

```bash
tar -czvf archive.tar.gz directory/
```

使用bzip2压缩归档文件：

```bash
tar -cjvf archive.tar.bz2 directory/
```
==提示：==
1. ==使用其他压缩算法需要的选项可使用--help或者man tar在终端查看==
2. ==因为-f是指定路径，所以在有多个选项时-f通常会放在最后==


## 2.2 查看文档
查看文档有多种方式：
1. cat
2. less
3. more
4. head
5. tail
所有的查看文档命令格式都为**主命令+文档路径**


各自特点：
1. cat命令会将文档中的内容一次性的输出到终端上面。所以一般适用小文件的查看
7. more命令将文档的内容按页进行输出。空格键进行翻页，b键返回上一页。输出完毕后，就会退出，文件内容残留在终端上。 
8. less命令将文档的内容是按页输出，空格翻页，也可以通过上下方向键按行输出，退出通过q来完成，而且退出后，终端没有文档内容残留。
9. head命令：通常会在主命令和文档路径之间加上 **“-n选项+显示行数”** 用来查看文档指定的前几行
10.tail命令：  通常会在主命令和文档路径之间加上 **“-n选项+显示行数”** 用来查看文档指定的后几行

## 2.3 主命令： find
find命令用于在Linux系统中查找文件和目录。它可以根据指定的条件搜索文件，并对搜索结果进行批量操作。

find的基本语法如下：

```bash
find [路径] [表达式]
```
下面是一些常用选项及其例子：
1. 搜索指定类型的文件：

```bash
find /path/to/directory -type f
```

上述命令将在 /path/to/directory 目录中搜索并列出所有的文件。

2. 根据文件名进行搜索：

```bash
find /path/to/directory -name "filename"
```

使用-name选项可以根据文件名进行搜索，可以使用通配符进行模糊匹配。如：“* name  ” “ * lena * ” “file*”

3. 搜索大于或小于指定大小的文件：

```bash
find /path/to/directory -size +100M
```

上述命令将搜索文件大小大于100MB的文件。+表示大于，-表示小于。

4. ==**在搜索结果中执行批量操作：**==

```bash
find /path/to/directory -name "*.txt" -exec rm {} \;
```

==上述命令将在 /path/to/directory 目录中搜索并删除所有扩展名为.txt的文件。-exec选项用于执行指定的操作，{}表示匹配的文件名，\;表示操作的结束。（这个操作很重要！）==

5. 搜索指定文件所有者的文件

```bash
find /path/to/directory -user root
```
上述命令将在/path/to/directory/目录中搜索文件所有者为root的文件

6. 根据文件权限搜索
6.1 搜索具有特定权限的文件：

```bash
find /path/to/directory -perm 644
```

上述命令将在/path/to/directory目录中搜索具有权限644的文件。
6.2 搜索具有至少一个指定权限的文件：

```bash
find /path/to/directory -perm /u=x
```

上述命令将在/path/to/directory目录中搜索至少具有用户可执行权限的文件。
6.3 搜索具有完全匹配权限的文件：

```bash
find /path/to/directory -perm -400
```

上述命令将在/path/to/directory目录中搜索具有完全匹配权限400的文件。
6.4搜索不具有指定权限的文件：

```bash
find /path/to/directory ! -perm 644
```

上述命令将在/path/to/directory目录中搜索不具有权限644的文件。

关于权限：
文件权限有：rwx三种以及特殊权限：SUID，SGID，Sticky
r：读权限
w：写权限
x：执行权限
SUID：当文件设置了SUID权限时，当任何用户执行该文件时，进程将以文件所有者的身份运行，而不是以执行者自己的身份运行。
SGID：当文件设置了SGID权限时，当任何用户执行该文件时，进程将以文件所属组的身份运行，而不是以执行者自己的身份运行。
Sticky：黏着位权限，当目录设置了粘着位权限时，在该目录下的文件只能由文件所有者或特定用户删除，其他用户没有删除权限。

一个文档如果没有加特殊权限，那么用数值表示该文件的权限时，将会是###三个数字，如果有特殊权限那么则变成####四个数字，第一个#是特殊权限位。

关于权限对应的数字：
r=4
w=2
x=1
SUID=4
SGID=2
Sticky=1

## 2.4 文本过滤命令
grep是一个在常用的命令，用于在文件或标准输入中搜索指定的模式。它使用正则表达式来进行模式匹配，并输出匹配到的行。
下面是grep命令的一般语法：

```bash
grep [options] pattern [file...]
```
其中：

1. options是一些额外的选项，用于指定不同的搜索行为，如忽略大小写、显示行号等。
2. pattern是要搜索的模式，可以是简单字符串或正则表达式。
3. file是要搜索的文件名。如果没有指定文件名，grep将会读取标准输入进行搜索。

选项    | 含义
-------- | -----
-i |忽略字母的大小写。
-v |反转匹配，只输出不匹配的行。
-r |递归搜索目录及其子目录中的文件。
-n |显示匹配行的行号。
-l |仅显示包含匹配项的文件名

示例：
1. 在文件中搜索包含特定字符串的行：

```bash
grep "pattern" filename
```

2. 忽略大小写，搜索包含特定字符串的行：

```bash
grep -i "pattern" filename
```

3. 递归搜索目录及其子目录中的文件：

```bash
grep -r "pattern" directory
```

4. 显示匹配行的行号：

```bash
grep -n "pattern" filename
```

## 2.5 管道符
管道符（|）是在Unix-like操作系统中用于连接多个命令的特殊符号。它的作用是将一个命令的输出作为另一个命令的输入，实现命令之间的数据传递和处理。
例如：

```bash
grep "pattern" filename | wc -l
```
其中，grep "pattern" filename用于搜索包含特定字符串的行，然后将结果通过管道传递给wc -l命令，用于统计行数。

## 2.6 重定向符
重定向符是在Unix-like系统中用于控制输入和输出的特殊符号。它们允许我们将命令的输入或输出从默认的位置重定向到文件或其他命令。

1. 标准输出重定向（>）：
语法：command > file
作用：将命令的标准输出（stdout）写入到指定的文件中。
注意事项：如果文件不存在，则创建新文件。如果文件已存在，则会覆盖原有内容。
2. 标准输出追加重定向（>>）：
语法：command >> file
作用：将命令的标准输出（stdout）追加写入到指定的文件中。
注意事项：如果文件不存在，则创建新文件。如果文件已存在，则在文件末尾追加新内容。
3. 标准错误输出重定向（2>或&>）：
语法：command 2> file
作用：将命令的错误输出（stderr）写入到指定的文件中。
注意事项：如果文件不存在，则创建新文件。如果文件已存在，则覆盖原有内容。
4. 标准错误输出追加重定向（2>>或&>>）：
语法：command 2>> file
作用：将命令的错误输出（stderr）追加写入到指定的文件中。
注意事项：如果文件不存在，则创建新文件。如果文件已存在，则在文件末尾追加新内容。
5. 标准输入重定向（<）：
语法：command < file
作用：将指定文件的内容作为命令的输入。
注意事项：如果文件不存在，则创建新文件。如果文件已存在，则会覆盖原有内容。

==注意：在重定向中有一个特殊路径：/dev/null，类似黑洞路由，无论什么消内容，指向该路径都不会保存在本地也不会输出在终端==

## 2.7 主命令：ln
ln命令是用于创建链接（link）的命令。它可以创建硬链接和符号链接（软链接/快捷方式）。

下面是ln命令的一般语法：

```bash
ln [options] <target> [linkname]
```

其中：
1. target是要链接的目标文件或目录。
2. linkname是新创建的链接文件的名称。

常见选项
项目     | Value
-------- | -----
-s |创建符号链接（软链接/快捷方式）。如果不指定此选项，默认创建硬链接。
-f |强制执行操作，即使目标文件已存在。
-i |在执行操作前进行确认提示。

一些命令示例：
1. 创建硬链接：

```bash
ln file.txt link.txt
```

这会在当前目录下创建一个名为link.txt的硬链接，指向file.txt。

2. 创建符号链接（软链接）：

```bash
ln -s file.txt link.txt
```

这会在当前目录下创建一个名为link.txt的符号链接，指向file.txt。

3. 创建目录的符号链接：

```bash
ln -s /path/to/directory linkdir
```

这会在当前目录下创建一个名为linkdir的符号链接，指向/path/to/directory目录。
==注意：硬链接是不可以对目录链接的，只有软连接才可以对目录链接==

4. 强制创建链接：

```bash
ln -sf file.txt link.txt
```

这会强制创建一个名为link.txt的符号链接，指向file.txt。如果link.txt已存在，会被覆盖。

软连接和硬链接的区别：
硬链接相当于一个备份，而软连接则是快捷方式，当文件本身被删除后，硬链接仍能打开，而软连接失效。

## 2.8 vim编辑器
emmm个人认为这个没有什么好说的。。。
格式就是

```bash
vim + 文件名
```
### 2.8.1 命令模式 
进入vim编辑器默认为命令模式，在命令模式下，从敲入的字符，变成具体特殊功能的命令，不能直接拿来进行编辑操作。
命令     | 含义
-------- | -----
ndd  |从光标处删除n行。
nyy   |   从光标处复制n行
p     |   粘贴
u     |   撤销
ctrl r |  反撤销

在vim中，光标只能通过上下左右方向键来移动，任何模式下，通过esc键返回命令模式，然后模式之间的切换也必须在命令模式下进行

### 2.8.2 编辑模式
在命令模式下，输入i/o/a/s都可以进入编辑模式，在编辑模式下，左下方会有-- INSERT –的提示。在编辑模式下，可以对文档进行编辑。（注意：在红帽操作系统7版本前，进行粘贴操作必须进入编辑模式）
命令     | 含义
-------- | -----
 i   |从光标处直接进入编辑模式
  o  | 从光标处另起一行进入编辑模式  
  a  | 从光标处的后一个字符进入编辑模式
s   |删除光标处的字符，并进入编辑模式

### 2.8.3 底行命令模式
在命令模式下，按“:”即可进入底行命令模式，左下方会出现一个“:”此刻便进入底行命令模式，然后输入的字符将变成具有特殊功能的命令。
项目     | Value
-------- | -----
:w |  保存
:q  | 退出 
:q! | 强制退出（不保存。！是强制的意思）
:wq | 保存并退出
:wq! | 强制保存并退出
: /+关键字| 查找关键字，所有和关键字匹配的字段都会被加上底色，按n键可以查找下一处 

## 2.9 管理本地用户和组
### 2.9.1本地用户介绍
在Linux系统中具有三种用户
1. 超级用户：管理员账号，root用户，权限最大，uid=0
2. 系统用户：系统用户是给软件进程使用的，权限较大，软件的资源调度就会使用到系统用户，0<uid<1000
3. 普通用户：由管理员创建，用来日常使用，权限较低，uid>1000

用户信息存放在/etc/passwd文件中
使用vim编辑器浏览文件内容可以发现每一行内容为一个用户
root用户存储的信息是这样的：

```yml
root:x:0:0:root:/root:/bin/bash
1...2.3.4.5....6.....7
```
我们使用root用户为例
在这一段信息中分为了七段，每一段之间使用“：”隔开
下面详细描述每一段的含义：
1. 用户名（Username）：表示用户的登录名。
2. 密码（Password）：在现代系统中，通常会使用“x”或“*”来表示密码已经存储在/etc/shadow文件中，而不是存储在/etc/passwd文件本身。这是由于安全性考虑。
3. 用户ID（User ID）：每个用户都被分配一个唯一的数字ID，称为用户ID或简称为UID。UID 0通常是root用户的特权UID。
4. 组ID（Group ID）：与用户相关联的原始组的数字ID，称为组ID或简称为GID。
5. 用户描述信息（User Description）：通常是用户的全名或其他相关信息。在登录界面出现的用户名其实就是这个信息
6. 用户主目录（Home Directory）：用户的主目录，也是用户登录后所在的起始工作目录。
7. 登录Shell（Login Shell）：用户登录后所使用的Shell程序。常见的有效登录Shell包括/bin/sh、/bin/bash、/bin/csh等。如果需要拒绝用户登录，你可以将其登录Shell设置为例如/bin/false或/usr/sbin/nologin。

### 2.9.2 管理用户
#### 2.9.2.1 主命令：useradd
useradd命令是创建新用户的命令。它允许系统管理员通过命令行创建新用户账户，并为其设置初始属性。

下面是useradd命令的一般语法：

```bash
useradd [options] username
```
其中：
1. username是要创建的新用户的用户名。
2. useradd命令的常见选项包括

部分选项：
选项     | 含义
-------- | -----
-m |同时创建用户的主目录。
-U |同时创建与用户名相同的新组，并将新用户添加到该组。
-s （shell） |指定用户的登录Shell。
-g （group）|指定用户的初始组。
-G （groups） |指定用户的附加组。
-p （password） |设置用户的密码。可以使用密码哈希值。
-d （home_directory） |指定用户的主目录路径。
-c （comment） |添加用户的注释信息。

#### 2.9.2.2 主命令：passwd
passwd命令是用于更改用户密码的命令。它允许用户或管理员通过命令行更改自己或其他用户的密码。

以下是passwd命令的一般语法：

```bash
passwd [options] [username]
```

其中：
username是要更改密码的用户的用户名。如果未指定用户名，则默认为当前用户。

部分选项：
选项 | 含义
----|----- 
-l |锁定用户密码，禁止用户登录。
-u |解锁（解除锁定）用户密码，允许用户登录。
-d |删除用户密码，允许无密码登录。
-e |强制用户在下次登录时更改密码。

==注意：==
1. 在root用户下，可以使用passwd  用户名 这种方式来给指定用户设置密码，而且密码的格式可以不受限制。
2. 如果普通用户的话，那么只能使用passwd来修改自己的密码，不能使用passwd + 用户名来对密码进行修改，而且普通用户下，密码的设置是有要求的，简单的密码，连续的密码，都是不能使用，而且密码必须8位以上。

#### 2.9.2.3 主命令：usermod
usermod命令是修改用户属性和设置的命令。它允许管理员通过命令行更改用户的登录Shell、主目录、用户组、注释等。

以下是usermod命令的一般语法：
```bash
usermod [options] username
```
其中：
username是要修改属性的用户的用户名。

常用选项：
选项 | 含义
----|----
-l （new_username） |修改用户的用户名。
-d （new_home_directory） |修改用户的主目录路径。
-s （new_shell） |修改用户的登录Shell。
-g （new_group）|修改用户的初始组。
-G （new_additional_groups） |修改用户的附加组。
-c （new_comment） |修改用户的注释信息。
-e （new_expire_date） |修改用户账户的过期日期。 

一些例子：
1. 修改用户的用户名：

```bash
sudo usermod -l new_username old_username
```

该命令将把名为old_username的用户的用户名修改为new_username。

2. 修改用户的登录Shell：

```bash
sudo usermod -s /bin/bash username
```

该命令将将名为username的用户的登录Shell更改为/bin/bash。

3. 修改用户的注释信息（用户描述）：

```bash
sudo usermod -c "John Doe - Sales Manager" username
```

该命令将名为username的用户的注释信息更改为"John Doe - Sales Manager"。

4. 修改用户的初始组和附加组：

```bash
sudo usermod -g new_primary_group -G new_additional_groups username
```

该命令将名为username的用户的初始组更改为new_primary_group，并将其附加组更改为new_additional_groups。附加组用逗号分隔。

==注意：usermod只能在管理员权限下使用==

#### 2.9.2.4 主命令：userdel
userdel命令用于删除用户账户。它允许管理员通过命令行删除用户的账户及相关文件。

以下是userdel命令的一般语法：
```bash
userdel [options] username
```
其中：
username是要删除的用户的用户名。

常见选项：
选项|含义
---|---
-r |删除用户的主目录和相关文件。
-f |强制删除用户，即使用户当前已登录。
-Z |删除用户的安全上下文（仅适用于SELinux）。

备注：一般情况下都是要加上-r对用户进行删除，如果没有加上-r,那么删除用户后，用户的家目录，邮箱目录里的数据依然会残留在系统中，导致数据安全的问题
如果忘记使用-r了，用户且已经删除，那么可以创建一个uid和用户名与残留数据用户一样的新用户，然后对新用户重新删除（加上-r）

### 2.9.3 组介绍
组是具有相同特征的一类用户的集合，便于对用户的批量管理。
在Linux中有两种组：
1. 主组
用户有且仅有一个主组，在创建用户的时候如果没有指定用户的主组，那么系统将会自动创建一个和用户名同名的组作为主组
2. 附加组
通俗来说，对于一个在多个组的用户来说，除了它的主组，其他的都算附加组

对于组来说，不管组本身是否是用户的主组，组所拥有的权限，组内用户都享有同样的权限

如何查看一个用户的组信息：
使用`id + 用户名`可以查看用户信息
这里使用root例子：

```yml
uid=1000(username) gid=1000(username) groups=1000(username),4(adm)
```
其中gid指明用户的主组为username
groups指明的是主组加上附加组，此处表明附加组为adm

组的信息保存在/etc/group
举个例子：

```yml
root:x:0:root
1...2.3.4
```
在/etc/group中也是一行一个组不同的字段使用“:”隔开

每段的详细信息：
1. 组名：组的名称。
2. 组密码：通常在现代系统中不常用，可以为空，或者是加密后的密码。
3. 组ID（GID）：唯一标识组的数字ID。
4. 组成员：组的成员列表，以逗号分隔。

### 2.9.4 管理组
#### 2.9.4.1 主命令：groupadd
groupadd命令用于添加一个新的用户组。它允许管理员通过命令行创建一个新的组，并分配一个唯一的组标识号（GID）。

以下是groupadd命令的一般语法：
```bash
groupadd [options] groupname
```
其中：
1. groupname是要创建的新组的名称。

常见选项：
选项|含义
---|---
-g （GID） |指定新组的组标识号（GID）。如果未指定，则系统将自动分配一个未使用的GID。
-r |创建一个系统组，其GID通常小于普通用户组的GID范围。

#### 2.9.4.2 主命令：groupmod
groupmod命令用于修改现有用户组的属性。它允许管理员通过命令行更改组的名称或组的标识号（GID）等属性。

以下是groupmod命令的一般语法：
```bash
groupmod [options] groupname
```

其中：
groupname是要修改的现有组的名称。

常见选项：
选项 | 含义
---|---
-n （newname） |指定现有组的新名称。
-g （newGID）|指定现有组的新组标识号（GID）。
-aG （groupname） |将用户添加到指定的附加组。
-G （grouplist） |用逗号分隔的组列表替换用户的附加组。

例子：
1. 将用户添加到一个附加组：

```bash
sudo usermod -aG groupname username
```

该命令将把名为username的现有用户添加到名为groupname的附加组。用户将会保留其原有的主要组。

2. 将用户从一个附加组中删除：

```bash
sudo gpasswd -d username groupname
```

该命令将从名为groupname的附加组中删除名为username的现有用户。

3. 替换用户的附加组列表：

```bash
sudo usermod -G grouplist username
```

该命令将用户的附加组列表替换为grouplist中的组列表。请注意，这会移除用户原来的附加组，并仅保留grouplist中指定的这些组。

#### 2.9.4.3 主命令：groupdel
groupdel命令用于删除一个用户组。它允许管理员通过命令行删除不再需要的组。

以下是groupdel命令的一般语法：

```bash
groupdel [options] groupname
```

其中：
groupname是要删除的组的名称。

groupdel命令没有选项：仅删除指定的组。

==注意：删除组时，请确保没有任何用户属于该组，即，确保该组为空。==