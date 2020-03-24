# Linux

### 知识

#### 历史

1969年由贝尔实验室开发UNIX

1991年10月5日，标志Linux诞生

#### GNU

角马 无版权

#### 体系结构

内核、命令解释层、实用工具

#### 内核版本

主版本号、次版本号、修正号

#### 发行版本

Red Hat、SUSE、Ubuntu、红旗Linux



### 基础

普通用户和root切换

```
su
```

如何修改配置，系统启动时默认进入字符界面？

```
vim /etc/inittab
id:5:initdefault 改成 id:3:initdefault
```

进入单用户模式

```
开机时 按"e"进入GRUB
再按"e"进入编辑
```

### 命令

身份

```
whomi
```

目录

```
pwd
ls
cd
cd    进入用户主目录；
cd ~  进入用户主目录；
cd -  返回进入此目录之前所在的目录；
cd ..  返回上级目录（若当前目录为“/“，则执行完后还在“/"；".."为上级目录的意思）；
cd ../..  返回上两级目录；
```

find

```
find [起始目录] 寻找条件 操作 
find –name ’tmp’  
-gid n 查找属于ID号为 n 的用户组的所有文件。
-uid n 查找属于ID号为 n 的用户的所有文件。
-group ’字串’ 查找属于用户组名为所给字串的所有的文件。
-user ’字串’ 查找属于用户名为所给字串的所有的文件。 
-perm 权限 查找具有指定权限的文件和目录，权限的表示可以如711，644。
-size n[bckw] 查找指定文件大小的文件，n 后面的字符表示单位，缺省为 b，代表512字节的块。 
-d 目录文件 


```

cp

```
cp(选项) 源文件 目标文件
-f：强行复制文件或目录，不论目标文件或目录是否已存在；
-l：对源文件建立硬连接，而非复制文件；

mv 参数 源文件 目标文件
-i 存在时是否覆盖
-f 直接覆盖

rm 参数 文件名
-i
-f
-R 删除里面的东西

touch 参数 文件名
-d yyyymmdd 时间为yyyy年mm月dd日
-a 存取时间改为当前
-m 修改时间改为当前

diff 参数 源文件 目标文件
-q 只报告不同地方
-i 忽略大小写

ln文件链接
ln [参数][源文件或目录][目标文件或目录]
-s 软链接(符号链接)

gzip压缩

gunzip解压

tar 解压
tar 参数 档案文件 文件列表
-z 以gzip格式
-x 解开档案文件

grep 查找文件中包含有指定字符的行
grep 参数 要查找字符 文件名
-c 计数
-i 忽略大小写
```

目录创建与删除

```
mkdir
rmdir
```

浏览文件

```
cat 参数 文件名
-b 非空标注行号
-n 全部行号

more一页一页显示文件

less

head开头

tail结尾
```



### more和less命令有何区别?

more不可以回去，就是不可以向前，只能向后，况且只能使用Enter和Space向后翻动。

less使用vim中的j，k键盘可以上下翻动，还可以使用上下箭头。

### Linux系统下对磁盘的命名原则是什么？

ide接口的硬盘用hd开头，其他接口用SD开头。第一块硬盘用a表示，第二块用b表示，以此类推。硬盘的第一个分区用1表示，第二个用2表示，第三个用3表示，以此类推。比如，sda1，表示sata接口上第一个硬盘的第一个分区。

### Vim的3种运行模式是什么？如何切换？

vi有三种工作模式：命令模式、文本编辑模式和最后行模式。

命令模式切换到文本编辑模式：i或者a

文本编辑模式切换到命令模式：Esc

命令模式切换到最后行模式：按“：”

最后行模式切换到命令模式：执行完后自动

### 什么是重定向？什么是管道？什么是命令替换？

重定向：不使用系统的标准输入端口、标准输出端口或标准错误端口，而进行重新的制定，所以重定向分为输入重定向、输出重定向和错误重定向。

管道：连接两个命令，把一个命令的输出作为另一个命令的输入。

命令替换：Shell中的命令参数可以由另一个命令执行的结果来替换。

### 如何建立和执行Shell脚本文件？如何使一个Shell脚本在当前Shell中运行？

**建立**

可以使用任何文本编辑器编辑shell脚本文件。

**执行**

**三种方法**

1将文件名作为shell命令参数

2将脚本文件权限改为可执行，再执行文件

3用“.”命令在当前shell中执行脚本命令

\#!/bin/sh

### 用户的管理

创建一个新用户user01，设置其主目录为/home/user01：　　

```
useradd –d /home/user01 -m user01
```

给用户user01设置密码：

```
passwd user01
```

查看passwd和shadow文件:

```
cat /etc/passwd
cat /etc/shadow
```

使用user01用户登录系统:

```
su user01
```

锁定用户user01:

```
passwd -l user01
```

解除对用户user01的锁定:

```
passwd -u user01
```

更改用户user01的帐户名为user02：

```
usermod –l user02 user01
```

删除用户user02：

```
userdel user02
```



### 组的管理

创建一个新组stuff：

```
groupadd stuff
```

查看group文件：

```
cat /etc/group
```

创建新帐户user03并把他的起始组和附属组都设为stuff：

```
useradd -g stuff -G stuff user03
```

给组stuff设置组密码：

```
gpasswd stuff
```

在组stuff中删除用户user03：

```
gpasswd -d user03 stuff
```

删除组stuff

```
sudo userdel user03
sudo groupdel stuff
```

### rpm软件包安装、卸载

安装

```
rpm -ivh
```

检测端口

```
netstat -an
```

查看IP

```
ifconfig
```

卸载

```
rpm -e ***
```

### 分区

创建

```
fdisk -l
```

格式化分区

```
mkfs -t test /dev/sdb1
```

挂载

```
mount /dev/sdb1
```



### 测试

新建用户lucy,uid为510，指定其所有组为group1，用户主目录为/home/lucy，用户密码为123456，账户永不过期：

```
useradd -u 510 -g group1 -d /home/lucy -p 123456 -f -1 lucy
```

将文件file1归属给用户lilei:

```
chown lilei /file
```

将test目录及其下的所有文件都归属到组group1:

```
chown -R : group1 /test
```

对普通用户创建的新目录，（ ）是默认的访问权限:

```
rwxrwxr-x
```

存放Linux基本命令的目录是:

```
/bin
```

如果umask设置为022，缺省的创建的文件的权限为:

```
rw-r--r--
```

现有一个外部设备文件，我们应该将其放在（ ）目录中:

```
/dev
```

如果user2想修改user1用户目录下的file1文件，应拥有( )权限:

```
664
```

修改文件file1权限为：所属账户具有读写权限，组用户和其它用户只有读权限:

```
chown 644 file1
```

在一个新分区上建立文件系统应该使用的命令是（）:

```
mkfs
```

挂载一个文件系统类型为fat32的U盘，其中U盘的设备名为/dev/hdb1,挂载点的路径为/mnt/u:

```
mount -t fat32 /dev/hdb1 /mnt/u
```

### vim

复制

```
yy拷贝当前行
y^
y$
yw
yG
```



粘贴

```
p  后
P  前
```

撤销

```
u 撤销（Undo）
U 撤销对整行的操作
Ctrl + r 重做（Redo），即撤销的撤销。


```

删除

```
x 删除当前字符
3x 删除当前光标开始向后三个字符
dd 删除当前行
D 删除当前字符至行尾
```

