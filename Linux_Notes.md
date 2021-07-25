---
title: "Linux_Notes"
date: 2021-03-31T20:21:29+08:00
draft: false
tags: ["Linux"]
categories: ["Linux"]
---

### 帮助命令

- man 帮助（manual 缩写）
  举例： man ls 获取 ls 命令的帮助
  man man 获取 man 命令的帮助，有很多重名的
  man 7 man 获取 man 命令第 7 章的命令
  man -a passwd 不清楚是 passwd 是配置、文件还是命令等，可以用-a 列出所有情况
  man -1 passwd 即获取 passwd 命令的帮助

- help 帮助
  shell 命令解释器自带的命令成为内部命令，其他的就是外部命令

如何区分内部、外部命令：
举例： type cd -> cd is a shell builtin cd 是内部命令
type ls -> ls is hashed (/bin/ls) ls 则是外部命令

举例： help cd 内部命令使用 help **
ls --help 外部命令使用 ** --help

### 开关机

- 关机：

```bash
shutdown -h now
shutdown -h 30
shutdown -c
```

- 重启：

```dotnetcli
reboot
shutdown -r now
shutdown -r 30
shutdown -c
```

- info 命令
  info 帮助比 help 更详细，作为 help 的补充。但 info 都是英文的。info 也比 man 要详细

### 切换图形界面：

init 3
init 5

### log out：

exit

### 常见的目录介绍：

- / 根目录
- /root root 用户的家目录
- /home/username 普通用户的家目录
- /etc 配置文件目录
- /bin 命令目录
- /sbin 管理命令目录
- /usr/bin /usr/sbin 系统预装的其他命令
- /dev 设备文件
- /dev/pts... 虚拟终端

### ls 查看当前目录下的文件

- ls [选项,选项... ] 参数 ...
- 常用用参数:
  - -l ⻓格式显示文文件
  - -a 显示隐藏文文件
  - -r 逆序显示
  - -t 按照修改时间顺序显示
  - -s 按容量顺序
  - -h 按人性化方式显示
  - -i 显示节点
  - -R 递归显示
  - -d 只显示目录本身信息，不包括其他内容
- ls -al 显示的信息含义

  - 第一列共 10 位，第 1 位表示文档类型，d 表示目录，-表示文件，l 表示链接文件，b 表示可随机存取的设备，如 U 盘等，c 表示一次性读取设备，如鼠标、键盘等。后 9 位，依次对应三种身份所拥有的权限，身份顺序为：owner、group、others，权限顺序为：readable、writable、excutable。如：-r-xr-x---的含义为当前文档是一个文件，拥有者可读、可执行，同一个群组下的用户，可读、可写，其他人没有任何权限。+表示设置了文件访问权限列表 属主与属组权限冲突以属主为主
  - 第二列表示链接数，表示有多少个文件链接到 inode 号码。
  - 第三列表示拥有者
  - 第四列表示所属群组
  - 第五列表示文档容量大小，单位字节
  - 第六列表示文档最后修改时间，注意不是文档的创建时间哦
  - 第七列表示文档名称。以点(.)开头的是隐藏文档

- #:代表是用管理员权限执行
- $:代表是用普通用户权限执行
-

```dotnetcli
pwd
file
```

### stat 查看文件详细信息

- stat + 文件或目录路径
  - Access 最近访问信息
  - Modify 最近更改信息 指文件内容
  - Change 最近改动 指文件属性
  - Birth 创建时间

### cd 更改当前的操作目目录

- cd /path/to/.... 绝对路路径
- cd ./path/to/... 相对路路径
- cd ../path/to/... 相对路路径

### mkdir 建立目目录

mkdir
常用用参数
-p no error if existing, make parent directories as needed

- 建立立目目录:

```dotnetcli
mkdir + 待创建目录
```

- 建立立多级目目录:

```dotnetcli
mkdir -p + 待创建目录
```

### 删除目录

- 删除空目录

```dotnetcli
rmdir + 待删除目录
```

- 删除非空目录

```dotnetcli
rm -r + 待删除目录
rm -rf + 待删除目录    # 删除前记得一定要反复检查 文件路径中不可以出现空格键 否则该文件路径会被rm指令当成两个路径 eg.`/a` and `/ a`
```

### 结束正在执行的命令

按 ctrl + c

### cp 复制文件和目录

- cp [选项] [文件或目录] [文件路径]
- cp [选项] [文件或目录] [文件路径】
- 通配符：`*`-多个字符 `?`-单个字符
- 常用参数
  - -r 复制目录
  - -p 保留留用户、权限、时间等文件属性
  - -a 等同于 -dpR
  - -v 显示复制过程

### mv 移动/重命名文件与目录

- mv [选项] 源文件 目标文件
- mv [选项] 源文件 目录

### Linus 下文件的命名规则：

### touch 命令

- touch 创建空白文件： `touch + filename`
- touch 修改文件时间戳
  _ touch 修改文件最近访问时间： `touch -a filename -t + "YYYYMMDDHHSS"` eg. 202005201314
  _ touch 修改文件最近更改时间： `touch -m filename -t + "YYYYMMDD"` eg. 202005201314
  _ touch 一次性修改文件的最近访问时间与最近更改时间: `touch -d "YYYYMMDD"` eg. 20200520 无指定具体时间，具体时间归零
  _ touch 无法人为修改最近改动时间
  注：rhel6 开始延迟修改

### 文本查看命令

- cat 文本内容显示到终端
- head 查看文件开头
- tail 查看文件结尾 \*常用参数 -f 文件内容更更新后,显示信息同步更新
- less
- more
- wc 统计文件内容信息
  - -l 查看文本一共有多少行

#### cat more less 区别：

cat 是一次性显示整个文件的内容，还可以将多个文件连接起来显示，它常与重定向符号配合使用，适用于文件内容少的情况；
more 和 less 一般用于显示文件内容超过一屏的内容，并且提供翻页的功能。more 比 cat 强大，提供分页显示的功能，less 比 more 更强大，提供翻页，跳转，查找等命令。而且 more 和 less 都支持：用空格显示下一页，按键 b 显示上一页。

### 打包与压缩命令

- 打包与解包
  - 最早的 Linux 备份介质是磁带,使用的命令是 tar
  - 可以打包后的磁带文文件进行行行压缩储存,压缩的命令是 gzip 和 bzip2
  - 经常使用的扩展名是 .tar.gz(.tgz) .tar.bz2(.tbz2)
  - Linux 一般备份/etc 文件 里面包含了 Linux 的主要配置文件
  - 常用参数：
    - `-c` 打包
    - `-x` 解包
    - `-f` 指定操作类型为文件
    - `-J` xz 格式压缩和解压缩
    - `-z` gzip 格式压缩和解压缩
    - `-j` bzip2 格式压缩和解压缩
    - `-v` 显示所有过程
    - `-C` change to directory DIR 后接需要解压到的目录 将 tar 包解压到该目录下
    - `-t` list the contents of an archive
    - `--exclude` 可以用来指定排除掉的文件目录
  - tar 命令的具体使用：
    - `tar -cf filename.tar filename` 打包 filename 文件为 filename.tar 文件
    - `tar -cJf filename.tar.xz filename` 打包并压缩 filename 文件为 file.tar.xz 文件
    - `tar -czf filename.tar.gz filename` 打包并压缩 filename 文件为 file.tar.gz 文件
    - `tar -cjf filename.tar.bz2 filename` 打包并压缩 filename 文件为 file.tar.bz2 文件
    - `tar -xf filename.tar filename` 解包 filename.tar 文件
    - `tar -xzf filename.tar.gz filename` 解压缩并解包 filename.tar.gz 文件
    - `tar -xjf filename.tar.bz2 filename` 解压缩并解包 filename.tar.bz2 文件
    - `tar -xJf filename.tar.xz filename` 解压缩并解包 filename.tar.xz 文件
    - `tar -xvf filename.tar.xz filename` 解压缩并解包 filename.tar.xz 文件
    - `tar -ztvf filename.tar.gz` 只列出包里的目录不解压解包
    - `tar -jtvf filename.tar.bz2` 只列出包里的目录不解压解包
    - `tar -Jtvf filename.tar.xz` 只列出包里的目录不解压解包
- 压缩与解压缩
  - 可以使用 xz gzip 和 bzip2 命令单独操作
  - 通常和 tar 命令配合操作
  - 常用用参数
    - -J xz 格式压缩和解压缩
    - -z gzip 格式压缩和解压缩
    - -j bzip2 格式压缩和解压缩
  - .zip 格式的压缩包的解压缩
    - -d 需要解压到的目录

## vi/vim - 强大的文本编辑器

- 四种模式
  - Normal-mode(正常模式)
    - h 光标向左
    - j 光标向下
    - k 光标向上
    - l 光标向右
    - x 删除光标所在字符
    - r 替换光标所在字符
    - 数字 n + G 跳转到 n 行
    - G 光标跳到最后一行
    - ^ 跳到行首
    - $ 跳到行尾
    - vim 内复制、粘贴、剪切
      - 复制(yank)
        - y 用 v 命令选中文本后，用 y 进行复制
        - yy 复制当前行，然后用 p 进行粘贴 前面可加数字 n,复制从当前行开始的 n 行
        - y$ 从当前位置复制到行尾
      - 粘贴(paste)
        - p(小写)在光标位置之后粘贴
        - P(大写)在光标位置之前粘贴
      - 剪切
        - d
        - dd
        - d$
      - 撤销
        - u 撤销
        - ctrl + r 撤销重做
    - 进入其他模式
      - i I a A o O 进入插入模式
      - v V ctrl + v 进入可视化模式
      - : 进入命令模式
      - esc 从其他模式回到正常模式
  - Inset-mode(插入模式)
    - i 光标位置不变
    - I 光标跳到行首
    - a 光标跳到下一个字符
    - A 光标跳到行尾
    - o 在光标所在行下方重起一行
    - O 在光标所在行上方重起一行
  - Command-mode(命令模式)
    - set nu 显示行号
    - set nonu 隐藏行号
    - q 退出
    - w 保存文件
    - wq 保存并退出
    - w + filename 保存文件并将文件命名为 filename
    - ! + 临时执行一条 Linux 命令
    - / + 字符串 搜索指定字符串
      - n 向下选中匹配到的字符串
      - N 向上选中匹配到的字符串
      - s/old/new 单次替换光标所在行匹配到的字符串
      - s/old/new/g 替换光标所在行所有匹配到所有字符串
      - %s/old/new/g 替换全文匹配到的所有字符串
      - m,ns/old/new 把第 m 行到第 n 行匹配到的字符串进行单次替换
      - m,ns/old/now/g 把第 m 行到第 n 行匹配到的所有字符串替换
  - Visual-mode(可视模式)
    - v 可视字符模式
    - V 可视行模式
    - ctrl + v 块可视模式(用的最多)
      - I 在选中的块前面添加字符 输入字符后按两次 esc
      - d 删除选中块
- 配置 vim

```dotnetcli
vim /etc/vim/vimrc
```

### 用户与权限管理

- 多用户操作系统
  - w 可得到当前用户的所有终端名称
  - tty 可得到当前登录的终端是哪个
  - 多用户操作系统的目的是隔离
    - 用户权限隔离
    - 系统资源隔离
- 用户管理常用命令
  - id + username 查看用户信息
  - useradd 新建用户
    - useradd + username 添加 username 用户 用户组名同用户名 系统自动创建/home/username 目录 并在该目录下自动生成用户配置文件 在/etc/passwd(用户管理信息)和/etc/shadow(与密码相关)添加一行以 username 开头的行 /etc/passwd 文件中各个字段名的意思---注册名：口令：用户标识号：组标识号：注释：用户主目录：命令解释程序 注意：如果 passwd 字段中的第一个字符是“\*”的话，那么，就表示该账号被查封了，系统不允许持有该账号的用户登录。现在的 Unix/Linux 系统中，口令不再直接保存在 passwd 文件中，通常将 passwd 文件中的口令字段使用一个“x”来代替，将/etc /shadow 作为真正的口令文件，用于保存包括个人口令在内的数据。当然 shadow 文件是不能被普通用户读取的，只有超级用户才有权读取。/etc/shadow 文件中字段主要含义为：登录名:加密口令:最后一次修改时间:最小时间间隔:最大时间间隔:警告时间:不活动时间:失效时间:标志 “登录名”是与/etc/passwd 文件中的登录名相一致的用户账号,“口令”字段存放的是加密后的用户口令字：如果为空，则对应用户没有口令，登录时不需要口令；星号代表帐号被锁定；双叹号表示这个密码已经过期了；$6$开头的，表明是用 SHA-512 加密；$1$表明是用 MD5 加密；$2$ 是用 Blowfish 加密；$5$ 是用 SHA-256 加密；“最后一次修改时间”表示的是从某个时刻起，到用户最后一次修改口令时的天数。时间起点对不同的系统可能不一样。例如在 SCOLinux 中，这个时间起点是 1970 年 1 月 1 日。“最小时间间隔”指的是两次修改口令之间所需的最小天数。“最大时间间隔”指的是口令保持有效的最大天数。“警告时间”字段表示的是从系统开始警告用户到用户密码正式失效之间的天数。“不活动时间”表示的是用户没有登录活动但账号仍能保持有效的最大天数。“失效时间”字段给出的是一个绝对的天数，如果使用了这个字段，那么就给出相应账号的生存期。期满后，该账号就不再是一个合法的账号，也就不能再用来登录了。
  - adduser + username 比 useradd 更加的好用
    [adduser 参考](https://opensofty.com/zh-cn/2019/11/18/%E5%A6%82%E4%BD%95%E5%9C%A8ubuntu-20.04%E4%B8%8A%E5%88%9B%E5%BB%BA%E6%96%B0%E7%94%A8%E6%88%B7/)
  - userdel 删除用户
    - userdel + username 删除用户的同时/home 下的用户数据会被保留下来
    - userdel -r + username 删除用户的同时/home 下的用户数据也会被删除
  - passwd 修改用户密码
    - passwd 修改当前用户的密码
    - passwd + username 修改 username 用户的密码
  - usermod 修改用户属性
    - usermod -d + dirname + username 把 username 用户的家目录设置为 dirname
    - usermod -g + groupname + username 将 username 添加到 groupname
  - chage 修改用户属性 对用户的生命周期进行修改
- 组管理命令
  - groupadd 新建用户组
    - groupadd + groupname 添加用户组<groupname>
    - usermod -g + groupname + username 将 username 添加到 groupname
  - groupdel 删除用户组
- 用户切换
  - su 命令
    - su USERNAME 切换用户
    - su - USERNAME 使用 login shell 方式切换用户
  - sudo 命令
    - sudo 以其他用户身份执行命令
    - visudo 设置需要使用 sudo 的用户(组)

### 用户的配置文件

- /root root 用户的家目录
- /home/USERNAME 普通用户默认家目录位置
- /etc/passwd 用户配置文件
  - /etc/passwd 文件中各个字段名的含义---用户名：口令：用户标识号：组标识号：注释：用户主目录：命令解释程序
  - 注意：如果 passwd 字段中的第一个字符是“\*”的话，那么，就表示该账号被查封了，系统不允许持有该账号的用户登录
  - 第二个字段为空时，登录免密，现在的 Unix/Linux 系统中，口令不再直接保存在 passwd 文件中，通常将 passwd 文件中的口令字段使用一个“x”来代替，将/etc /shadow 作为真正的口令文件，用于保存包括个人口令在内的数据。当然 shadow 文件是不能被普通用户读取的，只有超级用户才有权读取。
  - 第七个字段若为/sbin/nologin,则其无法登录
- /etc/shadow 用户密码相关配置文件

  - /etc/shadow 文件中字段主要含义为---登录名:加密口令:最后一次修改时间:最小时间间隔:最大时间间隔:警告时间:不活动时间:失效时间:标志
  - 登录名”是与/etc/passwd 文件中的登录名相一致的用户账号,“口令”字段存放的是加密后的用户口令字：如果为空，则对应用户没有口令，登录时不需要口令；星号代表帐号被锁定；双叹号表示这个密码已经过期了；
  - $6$开头的，表明是用 SHA-512 加密；$1$表明是用 MD5 加密；$2$ 是用 Blowfish 加密；$5$ 是用 SHA-256 加密；
  - “最后一次修改时间”表示的是从某个时刻起，到用户最后一次修改口令时的天数。时间起点对不同的系统可能不一样。例如在 SCOLinux 中，这个时间起点是 1970 年 1 月 1 日。
  - “最小时间间隔”指的是两次修改口令之间所需的最小天数。
  - “最大时间间隔”指的是口令保持有效的最大天数。
  - “警告时间”字段表示的是从系统开始警告用户到用户密码正式失效之间的天数。
  - “不活动时间”表示的是用户没有登录活动但账号仍能保持有效的最大天数。
  - “失效时间”字段给出的是一个绝对的天数，如果使用了这个字段，那么就给出相应账号的生存期。期满后，该账号就不再是一个合法的账号，也就不能再用来登录了。

- /etc/group 用户组配置文件
  - /etc/shadow 文件中字段主要含义为：用户组名：口令：组标识号(gid): 组内用户列表

### 文件权限的表示方法

- 字符权限表示方法
  - r 读
  - w 写
  - x 执行
- 数字权限的表示方法
  - r = 4
  - w = 2
  - x = 1
- 创建新文件有默认权限，根据 umask 值计算，属主和属组根据当前进程的用户来设定
- ls -al 显示的信息含义
  - 第一列共 10 位，第 1 位表示文档类型，d 表示目录，-表示文件，l 表示链接文件，b 表示可随机存取的设备，如 U 盘等，c 表示一次性读取设备，如鼠标、键盘等。后 9 位，依次对应三种身份所拥有的权限，身份顺序为：owner、group、others，权限顺序为：readable、writable、excutable。如：-r-xr-x---的含义为当前文档是一个文件，拥有者可读、可执行，同一个群组下的用户，可读、可写，其他人没有任何权限。
  - 第二列表示链接数，表示有多少个文件链接到 inode 号码。
  - 第三列表示拥有者
  - 第四列表示所属群组
  - 第五列表示文档容量大小，单位字节
  - 第六列表示文档最后修改时间，注意不是文档的创建时间哦
  - 第七列表示文档名称。以点(.)开头的是隐藏文档
- 当属主权限与属组权限冲突时以文件的属主权限为主

### 目录权限的表示方法

- r 拥有此权限表示可以读取此目录的结构列表，也就是说可以查看该目录下的文件名和子目录名（ls 查看）
- w 可以在此目录中创建文件，也可以删除、重命名移动文件
- x 具有进入此目录的权限

### 修改权限命令

- chmod 修改文件、目录权限
  - chmod u+x /tmp/testfile 属主加上执行权限
  - chmod g-r filename 同组用户减少读权限
  - chmod u=rwx filename 属主加上读写执行命令权限
  - chmod a+r filename 属主同组用户包括其他用户全都加上读权限
  - chmod 755 /tmp/testfile
- umask
- 创建新文件/文件夹有默认权限，根据 umask 值(root 用户默认为 0022，普通用户默认为 0002)计算，文件默认权限为 0666-umask，文件夹默认权限为 0777-umask 属主和属组根据当前进程的用户来设定
- chown 更改属主、属组
  - chown username filename 把文件 filename 属主改为 username
  - chown :groupname filename 把文件 filename 属组改为 groupname
  - chown username:groupname filename 同时对属主与属组进行修改 把文件 filename 属主改为 username 把文件 filename 属组改为 groupname
- chgrp 可以单独更改属组 不常用
  - chgrp groupname filename 把文件 filename 属组改为 groupname
- root 用户有特权即使没有权限也可以执行 rwx 操作

### 特殊权限

- 特殊权限的数字表示法
  - SUID=4
  - SGID=2
  - SBIT=1
- 特殊权限的字符表示法
  - SUID s
  - SGID s
  - SBIT t
- SUID 用于二进制可执行文件，执行命令时取得文件属主的权限(SUID 权限仅对二进制可执行文件有效，当二进制文件权限信息的第四个字段为 s 时且执行者对于该二进制可执行文件具有 x 的权限，执行者将具有该文件的所有者的权限，该权限仅在执行该二进制可执行文件的过程中有效)
  - 如/usr/bin/passwd
  - chmod 4755 filename
- SGID 用于二进制可执行文件(同 SUID)，也可用于目录，在该目录下创建新的文件和目录，权限自动更改为该目录的属组(常用于文件共享，用户若对此目录具有 r 和 x 权限，该用户能够进入该目录，用户在此目录下的有效用户组将变成该目录的用户组，若用户在此目录下拥有 w 权限，则用户所创建的新文件的用户组与该目录的用户组相同)
  - chmod 2755 filename
- SBIT 用于目录，该目录下新建的文件和目录，仅 root 和自己可以删除(文件权限信息的最后一个字段为 t,SBIT 是 the restricted deletion flag or sticky bit 的简称,SBIT 目前只对目录有效，用来阻止非文件的所有者删除文件)
  - 如/tmp
  - chmod 1755 filename

### 命令或命令文档定位

- which locate a command

- whereis locate the binary, source, and manual page files for a command

- locate

- find

  ```bash
  find <DirName> -type f	# 查看一个文件下有多少文件
  ```

## Linux 系统管理

- 网络状态查看
  net-tools VS iproute

  - net-tools (centOS7 前)

    - ifconfig

      - eth0 第一块网卡(网络接口)
      - 你的第一个网络接口可能叫做下面的名字
        - eno1 板载网卡
        - ens33 PCI-E 网卡
        - enp0s3 无法获取物理信息的 PCI-E
        - CentOS 7 使用了一致性网络设备命名，以上都不匹配则使用 eth0
      - 网络接口命名修改
        - 网卡命名规则受 biosdevname 和 net.ifnames 两个参数影响
        - 编辑/etc/default/grub 文件，增加 biosdevname=0 net.ifnames=0
          - 默认 biosdevname=0 net.ifnames=1 网卡名为 ens33
          - 组合一 biosdevname=1 net.ifnames=0 网卡名为 em1
          - 组合二 biosdevname=0 net.ifnames=0 网卡名为 eth0
        - 更新 grub `grub2-mkconfig -o /boot/grub2/grub.cfg`
        - 重启 `reboot`
      - 普通用户用 ifconfig 命令查看用户网卡信息要给出完整的 ifconfig 命令文件路径 /sbin/ifconfig
        - 本机网卡信息
          - inet 网卡的 iPv4 地址
          - inet6 网卡的 iPv6 地址
          - netmask IP 地址对应的子网掩码
          - ether 网卡的 MAC 地址
          - RX 接收了多少数据包
          - TX 发送了多少数据包
        - lo 本地的环回
          - inet iPv4 地址永远是 127.0.0.1 用于环回测试

    - route 查看网关
      - route -n 使用 -n 参数不解析主机名
    - netstat

  - iproute2 (centos7 后)
    - ip
      - ip addr
    - ss
  - mill-tool eth0 查看网卡物理连接情况

- 网络配置
  - ip addr add <ip 地址/掩码位>
  - ifconfig <接口> <ip 地址> [netmask 子网掩码]
  - ifup <接口>
  - ip link set dev eth0 up
  - ifdown <接口> ifdown ifup 可以重置网卡为默认值
  - ip link set dev eth0 down
- 路由命令
  - 添加网关
    - route default gw <网关 ip>
    - route add -host <指定 ip> gw <网关 ip>
    - route add -net <指定网段> netmask <子网掩码> gw <网关 ip>
    - ip route add <指定 ip 地址/掩码位> via <网关 ip>
- 网络故障排除
  - ping 查看当前主机与目标主机网络是否连通
  - traceroute 检测当前主机与目的主机网络的连接状况 追踪每一跳的服务质量 辅助 ping 来使用
  - mtr 检测当前主机与目的主机网络之间的传送中间是否有些数据包给丢失了 辅助 ping 来使用 显示内容比 traceroute 更丰富
  - nslookup 查看域名对应的 ip 输入 server 查看 DNS exit 退出
  - dig
  - telnet 主机能够连接但依旧不能连接 查看端口的连接状态 ctrl + ] 退出查看 输入 quit 退出 telnet
  - tcpdump 网络抓包服务 分析数据包
    - tcpdump -i any 抓取所有网卡中的数据包
    - tcpdump -i any -n 抓取所有网卡中的数据包 把有域名的都解析成 ip 地址格式
    - tcpdump -i any -n port <端口号> 抓取所有网卡中<端口号>端口的数据包
    - tcpdump -i any -n host <ip 地址> 抓取从我的主机到<ip 地址>的所有数据包
    - tcpdump -i any -n host <ip 地址> and port <端口号> 抓取从我的主机到<ip 地址>的<端口号>端口的所有数据包
    - tcpdump -i any -n host <ip 地址> and port <端口号> -w /tmp/filename 抓取从我的主机到<ip 地址>的<端口号>端口的所有数据包并保存到/tmp/filename
  - netstat -ntpl 查看服务的监听范围
    - -n 显示 ip 地址
    - -t 以 tcp 的方式来截取我们想要显示的内容，udp 就不显示了
    - -p 把端口对应的进程也显示出来
    - -l tcp 的一个状态
  - ss -ntpl 查看服务的监听范围 与 netstat 相似
- 网络服务管理
  - SystV
    - service network start|stop|restart
    - chkconfig --list network
    - chkconfig --level <服务级别> network off
  - systemd
    - systemctl list-unit-files [<packagename>] // 可以查看是否设置为开机自启动
    - systemctl start|stop|restart <packagename>
      - systemctl systemctl enable|disable <packagename> // 设置是否开机自启动
- 常用网络配置文件
  - /etc/sysconfig/network-scripts/
  - ifcfg-eth0
    - BOOTPROTO
      - "dhcp" 动态分配 IP 自动获取 ip 地址
      - "static"或 none 静态分配 IP
        - IPADDR
        - NETMASK
        - DNS1 DNS2 DNS3
    - NAME 和 DEVICE 表示的是网络的设置
    - ONBOOT
      - "yes"开机的时候网卡会被自动启用
      - "no"开机的时候网卡不会被自动启用
  - hostname <newhostname> 将主机名改为<newhostname> 临时生效
  - /etc/hosts 很多服务依赖于主机名进行服务的,所以主机名改变后,要将 `127.0.0.1 <newhostname>` 写入/etc/hosts 中 否则可能会导致系统开机过慢(系统服务无法从 hosts 解析 IP 只能等待超时)
  - systemctl restart NetworkManager o service network restart 重启生效
  - hostnamectl set-hostname <newhostname> 永久更改 hostname 接着需要修改/etc/hosts 文件

### 软件安装

- 软件包管理器
  - 包管理器是方便软件安装 装载,解决软件依赖关系的重要工具
  - CentOS RedHat 使用 yum 包管理器,软件安装包格式为 rpm
  - Debian Ubuntu 使用 apt 包管理器,软件安装包为 deb
- rpm 包与 rpm 命令
  - rpm 包 软件名称 软件版本 系统版本 平台
  - rpm 命令常用参数
    - -qa 系统安装的所有 rpm 软件包
    - -q 查询软件包
    - -i 安装软件包
    - -e 卸载软件
- mount 挂载光盘
  - mount <光盘路径> /mnt 把<光盘路径>挂载到/mnt
- yum 仓库/管理器
  - rpm 包的问题
    - 需要自己解决依赖问题
    - 软件包来源不可靠
  - CentOS yum 源
    - [国外官方源](http://mirror.centos.org/centos/7/)
    - [阿里云源配置指南](https://developer.aliyun.com/mirror/centos?spm=a2c6h.13651102.0.0.3e221b11hNsKC1)
  - yum 命令常用选项
    - install 安装软件包
    - remove 卸载软件软件包
    - list|grouplist 查看软件包
    - update 升级软件包
  - yum install epel-release -y // 安装 epel 仓库
- 源代码编译安装
  - 二进制安装
  - 源代码编译安装
    - wget <下载地址>
    - tar -zxf <ResourceCodeName.tgz>
    - cd ResourceCodeName/
    - ./configure --prefix=/usr/localResourceCodeName // 匹配安装环境 --prefix 指定安装目录
    - yum install gcc gcc-g++ 若没有安装 gcc gcc-g++
    - make -j2 或 gmake -j2(跨平台编译) // 把源代码编译为可执行程序 -j2 表示用两个逻辑内核参与编译
    - make install 把编译好的二进制文件安装到指定环境
    - 卸载的时候把软件的安装目录删除掉就可以了
- 内核升级
  - rpm 格式内核
    - uname -r 查看内核版本
    - yum install kernel // 升级内核
    - yum install kernel-x.xx.x // 安装 or 升级指定内核版本
    - yum update 升级内核及已安装的其他软件包和补丁
    - yum install epel-release -y // 安装 epel 仓库
  - 源代码编译安装
    - 编译安装内核要确保/分区有 10g 以上的容量,否则可能会出现安装失败的情况
    - yum install gcc gcc-g++ make ncurses-devel openssl-devel elfutils-libelf-devel 安装依赖包
    - [下载内核](https://www.kernel.org)
    - tar -C /usr/src/kernels -Jxvf linux-x.xx.xx.tar.gz
    - cd /usr/src/kernels/linux-x.xx.xx.tar.gz && make menuconfig | allyesconfig | allnoconfig // 配置内核编译参数 menuconfig:自己通过菜单配置 allyescondfig:自动配置都安装 allnoconfig 最小配置,可能连启动都启动不了
    - cp /boot/config-kernelversion.platform /urs/src/kernels/linux-5.x.xx.xx/.config // 使用当前系统内核配置
    - lscpu 查看 cpu
    - make -j2 all // 对所有的编译选项进行编译
    - make modules_install && make install // 先自动安装内核支持的模块 然后再安装内核 并自动修改启动文件
- grub 配置文件
  - /etc/default/grub
    - grub2-editenv list // 列出系统默认启动的内核
    - grep ^menu /boot/grub2/grub.cfg // 列出所有内核的名称
    - grub2-set-default <行数> // 设置系统默认启动的内核
    - /etc/default/grub 中的 GRUB_CMDLINE_LINUX 添加的是 linux 内核引导的过程中对内核增加的参数
      - rhgb 图形界面
      - quiet 静默模式 引导的时候只是打印必要的消息 如果我们发现启动异常的时候我们一般把 quiet 去掉 把 rhgb 和 quiet 去掉我们可以发现引导的时候系统打印更详细的消息
  - /etc/grub.d/
  - /boot/grub2/grub.cfg
  - /grub2-mkconfig -o /boot/grub2/grub.cfg
  - 忘记 root 密码的情况下修改 root 密码 做笔记比较耗时间 先放着 具体请参考 极客时间 Linux 实战技能 100 讲 36|grub 配置文件介绍 [鸟哥的 Linux 私房菜参考](http://linux.vbird.org/linux_basic/0510osloader.php#solution_root)

### 进程管理

- 进程的概念与进程查看
  - 进程---运行的程序，从程序开始运行到终止的整个生命周期是可管理的
    - 守护进程已经完全脱离终端控制台了，而后台程序并未完全脱离终端，在终端未关闭前还是会往终端输出结果
    - 守护进程在关闭终端控制台时不会受影响，而后台程序会随用户退出而停止，需要在以 nohup command & 格式运行才能避免影响
  - c 程序的启动是从 main 函数开始的
  - 终止的方式并不唯一， 分为正常终止和异常终止
    - 正常终止也分为从 main 返回 调用 exit 等方式
    - 异常终止分为调用 abort 接收信号等
  - 进程也是树形结构
  - 进程和权限有着密不可分的关系
  - ps ps 不带任何参数 列出当前终端执行的命令进程
  - ps -e | more 1 号进程是 systemd 旧的 linux 1 号进程可能是 init
  - ps -ef | more 比 ps -e 显示更多的消息 这里 UID 叫做有效用户 id UID 显示的不一定是启动进程的用户也有可能显示 nobody 进程启动后 UID 可能发生更改 PPID：父进程 LWP：线程数 TTY 表示控制终端，若显示为？则表示没有控制终端；TIME 表示占用的 CPU 时间；CMD 表示执行的命令
  - pstree | more
  - top
    - top -p <PID> 只显示<PID>进程的相关信息
    - 第一行(top...)：这一行显示的资讯分别为：
      - 目前的时间
      - 开机到目前为止所经过的时间
      - 已经登入系统的使用者人数
      - 系统在 1, 5, 15 分钟的内的平均工作负载 越小代表系统越闲置，若高于 1 得要注意你的系统程序是否太过繁复了！
    - 第二行(Tasks...) 显示的是目前程序的总量与程序在各种状态(running, sleeping, stopped, zombie)的数量 比较需要注意的是最后的 zombie 那个数值，如果不是 0 ！好好看看到底是那个 process 变成僵尸了吧？
    - 第三行(%Cpus...)：显示的是 CPU 的整体负载，每个项目可使用? 查阅。(要特别注意的是 wa 项目，那个项目代表的是 I/O wait， 通常你的系统会变慢都是 I/O 产生的问题比较大！因此这里得要注意这个项目耗用 CPU 的资源喔！另外，如果是多核心的设备，可以按下数字键『1』来切换成不同 CPU 的负载率。
      - us user 表示用户态的 CPU 时间比例
      - sy system 表示内核态的 CPU 时间比例
      - ni nice 表示运行低优先级进程的 CPU 时间比例
      - id idle 表示空闲 CPU 时间比例
      - wa iowait 表示处于 IO 等待的 CPU 时间比例
      - hi hard interrupt 表示处理硬中断的 CPU 时间比例
      - si soft interrupt 表示处理软中断的 CPU 时间比例
      - st steal 表示当前系统运行在虚拟机中的时候，被其他虚拟机占用的 CPU 时间比例。
    - 第四行与第五行：表示目前的实体记忆体与虚拟记忆体(Mem/Swap) 的使用情况。再次重申，要注意的是 swap 的使用量要尽量的少！如果 swap 被用的很大量，表示系统的实体记忆体实在不足！
    - 第六行：这个是当在 top 程式当中输入指令时，显示状态的地方。
      PID 进程 ID
    - 第七行
      - USER 进程所有者的用户名，例如 root
      - PR 进程调度优先级
      - NI 进程 nice 值(优先级)，越小的值代表越高的优先级
      - VIRT 进程使用的虚拟内存
      - RES 进程使用的物理内存（不包括共享内存）
      - SHR 进程使用的共享内存
      - %CPU 进程使用的 CPU 占比
      - %MEM 进程使用的内存占比
      - S 进程状态
        - S 睡眠
        - R 运行
        - D 不可中断的睡眠状态
        - Z 僵尸进程
        - T 跟踪/停止 挂起状态 程序保存在内存中 作业处于暂停状态
      - TIME+ 进程启动后到现在所用的全部 CPU 时间
      - COMMAND 进程的启动命令（默认只显示二进制，top -c 能够显示命令行和启动参数）
    - 预设更新程序资源的时间为 3 秒可以按 s 切换采集频率
- 进程的控制命令
  - 调整优先级别
    - nice 范围从-20 到 19 值越小优先级越高 抢占资源就越多
      - nice -n <nice 值> <可执行文件> // 将<可执行文件>的的优先值设置为<nice 值>
    - renice 重新设置优先级
      - renice -n <nice 值> <可执行文件> // // 将<可执行文件>的的优先值重新设置为<nice 值>
  - 进程的作业控制
    - jobs
      - jobs -l // 列出后台的工作状态 同时列出后台任务的 pid
      - jobs -r // 仅列出正在后台 run 的工作
      - jobs -s // 仅列出正在后台中暂停(stop) 的工作
    - & 符号 // 命令后加& 把进程切换到后台
    - jobs 查看切换到后台的任务
    - fg [job_spec ...] // 把任务切换到前台
    - bg [job_spec ...] // 把任务切换到后台运行
    - ctrl-z // 把程序进行临时的挂起
    - ctrl-c // kill foreground process
    - ctrl-d // Terminate input, or exit shell 一个特殊的二进制值，表示 EOF，作用相当于在终端中输入 exit 后回车
    - ctrl-/ 发送 SIGQUIT 信号给前台进程组中的所有进程，终止前台进程并生成 core 文件
    - ctrl-s 中断控制台输出
    - ctrl-q 恢复控制台输出
    - ctrl-l 清屏
- 进程的通信方式-信号
  - 信号是进程间通信方式之一,典型用法是: 终端用户输入中断命令,通过信号机制停止一个程序的运行。
  - 使用信号的常用快捷键和命令
  - kill -l // 列出所有支持的信号
    - ctrl-c // SIGINT 通知前台进程组终止进程
    - kill -15 <pid> // SIGTERM 执行 kill（不加 -\* 默认 kill -15）命令,系统会发送一个 SIGTERM 信号给对应的程序,当程序接收到该 signal 信号后,将会发生以下事情：1.程序立刻停止 2.当程序释放相应资源后再停止 3.程序可能仍然继续运行 大部分程序接收到 SIGTERM 信号后，会先释放自己的资源，然后再停止。但是也有程序可能接收信号后，做一些其他的事情（如果程序正在等待 IO，可能就不会立马做出响应，我在使用 wkhtmltopdf 转 pdf 的项目中遇到这现象），也就是说，SIGTERM 多半是会被阻塞的。
    - kill -9 <pid> // SIGKILL 即 exit exit 信号不会被系统阻塞 所以能立即结束程序,不能被阻塞和处理 最好别使用 不要使用 kill -9 它没有给进程留下善后的机会：1.关闭 socket 链接 2.清理临时文件 3.将自己将要被销毁的消息通知给子进程 4.重置自己的终止状态
- 守护进程和系统日志

  - 使用 nohub 与&符号配合运行一个命令
    - nohub 命令使进程忽略 hangup(挂起)信号 即使终端关掉 进程依旧可以运行 忽略输入并把输出追加到"nohub.out" 终端关掉后父进程关闭 该进程变为孤儿进程 所以父进程 PPID 变为 1
      - nohub tail -f /var/log/messages
      - cd /proc/<PID> && ls // 列出的目录就是文件的属性
      - ls /proc/<PID>/cwd // 当前所在的位置
      - ls /proc/<PID>/fd // 输出的存放位置
        - 0 表示标准输入
        - 1 和 2 表示标准输出
  - 守护进程(daemon)和一般进程有什么区别？

    - cd /proc/<PID> && ls // 列出的目录就是文件的属性
    - ls /proc/<PID>/cwd // 当前所在的位置 nohub 是用户主目录 daemon 是/(根目录)
    - ls /proc/<PID>/fd // 输出的存放位置 nohub 和 daemon 输出的位置不一样 nohub 输出到 nohub.out 中 daemon 通过 socket 输出到系统日志程序然后打印到/var/log/ <pid>服务对应的日志文件中
      - 0 表示标准输入
      - 1 和 2 表示标准输出 // nohub 输出到 nohub 中 daemon 通过 socket 输出到系统日志程序然后打印到/var/log/ <pid>服务对应的日志文件中

  - 使用 screen 命令
    - screen 进入 screen 环境 // 进入 screen 后即使网络断开了依旧还是可以保留工作现场,待下次重新连接后可以恢复工作现场,规避因网络中断造成的网络异常
    - ctrl+a d 退出(detached)screen 环境
    - screen -ls 查看 screen 的会话
    - screen -r <sessionid> 恢复会话
    - exit 退出 screen 环境
  - 系统日志
    - cd /var/log && ll // 系统日志 系统运行的状态会打印到这些日志文件中
    - tail -f ./message // 系统常规日志 系统出现的一系列异常 message 都会打印到 message 里 所以 server 中 message 出现了内容 我们需要进行及时的处理
    - tail -f ./dmesg // dmesg 是内核运行的相关信息 一般是内核启动过程中打印进来的
    - tail -f ./secure // 系统的安全日志信息
    - tail -f ./cron // 系统执行周期性计划任务的一些日志信息

- 服务管理工具 systemctl
  - 服务(提供常见功能的守护进程)集中管理工具
    - service // 优点: 执行起来比较简单 缺点: 每一个包括 star|stop|restart 都需要自己来编写脚本来实现 服务控制的好坏完全由编写 star|stop|restart 脚本的人来控制
      - cd /etc/init.d/ && ll
      - 服务级别
        - init 0 // 关机 1 号进程 init 不能被 kill -9 关闭 常用
        - init 1 // 单用户 只允许 root 用户对系统进行维护
        - init 2 // Multi-user mode without network services started 不带网络的多用户模式
        - init 3 // Multi-user mode with network services started 最常用的字符模式 多用户
        - init 4 // 系统未使用，保留
        - init 5 // 多用户 GUI 模式
        - init 6 // 重启 常用
    - sytemctl // service 的强化
      - cd /usr/lib/systemd/system/ && ll
        - ExecStart // start
        - Restart // restart
      - systemctl list-dependencies [target]
      - sytemctl 常见操作
        - systemctl start|stop|restart|reload|enable|disable <ServiceName>
          - start // 开启服务
          - stop // 关闭服务
          - restart // 把服务停掉再重启
          - reload // 服务不停 只从加载配置文件
          - enable // 开机自启动
          - disable // 禁止开机自启
        - systemctl status <ServiceName> // 查看<ServiceName>的服务状态
        - systemctl list-unit-files // 查看 Service 是否开机自启
        - 软件包安装的服务单元 /usr/lib/systemd/system/
        - 服务级别
          - systemctl get-default // 系统当前服务级别
          - systemctl set-default <TargetName> // 改变服务级别 下次启动时生效
          - 服务启动的顺序问题 在[Unit] After 中修改 并加上 Requires
          - [Install] 在哪一个 target 会被默认引导
          - cd /usr/lib/systemd/system && ll
          - ll \*.target
          - ll runlevel\*.target
- selinux 简介 // 安全性高但是会影响性能 所以生成环境上 selinux 大部分情况下都是关闭的
  - MAC(强制访问控制)与 DAC(自主访问控制)
  - 查看 SELinux 的命令
    - getenforce
    - vim /etc/selinux/config // 修改后需要重启
    - /usr/sbin/sestatus
    - ps -Z and ls -Z and id -Z // 查看具体的标签
  - 关闭 SELinux
    - setenforce 0 // 将 Enforcing 临时的改变为 Permissive 重启后恢复为 Enforcing
    - /etc/selinux/sysconfig

### 内存与磁盘管理

- 内存和磁盘使用率查看
  - 内存使用率查看
    - free
      - free -h // show human-readable output
      - free -m // 以 MiB 的形式显示
      - free -g // 以 GiB 的形式显示 取整
    - top
  - 磁盘使用率查看
    - ll /dev/sd? // 查看磁盘,第 5 第 6 字段分别用来表示磁盘的主设备号和从设备号 主设备号用来表示磁盘用什么样的驱动程序 从设备号用来确定访问什么样的地址
    - ll /dev/sd?? // 如果磁盘有分区的话查看磁盘及分区
    - fdisk
      - fdisk -l 查看磁盘信息
      - parted -l 和 fdisk -l 差不多
    - df
      - df -h
    - du
    - du 与 ls 的区别 // du 列出实际占用大小 ls 列出的是文件大小 du 统计的是数据块里面的信息 ls 统计的是 i 节点里面的信息
    - dd if=<afile> bs=4M count=10 seek=20 of=<bfile> // 先创建一个 bfile 的文件 按照 4M 为一个块 然后跳过 20 块 拷贝 10 次
    - dd if=/dev/zero bs=4M count=10 seek=20 of=<bfile> // 先创建一个 bfile 的文件 按照 4M 为一个块 然后跳过 20 块 拷贝 10 次 // 用于 Linux 上磁盘的虚拟化
- ext4 文件系统
  - Linux 支持多种文件系统,常见的有
    - ext4 // ext4 文件系统基本结构比较复杂
      - 超级块 // 位于文件系统最开头的位置 记录了文件系统中包含了多少个文件
      - 超级副本 // 不只一个备份
      - i 节点(inode) // 记录每一个文件的名称 大小 编号 权限等信息 每个文件的文件名没有记录在自己的 i 节点上 记录在该文件父目录的 DataBlock 节点上
      - 数据块(datablock) // 记录数据
      - cp
      - mv 如果只是改名的话 数据块节点不变 只有父目录节点上的文件名发生改变 如果是移动到别的目录若移动到其他分区则数据块节点会变化,花费时间较长,若移动到本分区内,也是瞬间完成的,数据块节点不发生改变
      - echo "Content" > <FileName> and echo "Content" >> <FileName> // echo 对文件进行写入的时候 i 节点不会发生改变 用 vim 对文件写入的时候 i 节点会发生改变, >为覆盖写入 >>为追加写入
      - rm // 实际就是让文件名与 i 节点的链接断开 这样做的好处是不管删除多大的文件所需时间都是一样的 也方便找回数据
      - 硬链接不能跨越分区 软链接(符号链接)可以跨越分区
      - facl 文件访问控制列表
        - getfacl 查看文件访问控制列表
        - setfacl -m 授予文件访问权限
          - setfacl -m u:<username>:<r|w|x> <filename>
          - serfacl -m g:<groupname>:<r|w|x> <filename>
          - 在 rules 前加一个 d:，以表示指定一个目录
        - setfacl -x 回收文件访问权限
          - setfacl -x u:<username>:<r|w|x> <filename>
          - serfacl -x g:<groupname>:<r|w|x> <filename>
    - xfs
    - NTFS(需安装额外软件)
- 磁盘配额的使用
  - xfs 文件系统的用户磁盘配额 quota
  - mkfs.xfs </dev/PartitionName>
  - mkdir </mnt/PartitonName>
  - mount -o uquota,guota </dev/PartitionName> </mnt/PartitionName> // uquota:用户磁盘配额 gquota:组磁盘配额
  - mount 查看挂载情况
  - vim /etc/fstab
  - chmod 1777 </mnt/PartitonName>
  - xfs_quota -x -c 'report -gibh' </mnt/PartitonName>
  - xfs_quota -x -c 'limit -u isoft=5 ihard=10 <UserName>' </mnt/PartitonName> // 对 i 节点进行限制 软限制:在限定时间内允许超过一定的值 硬限制:不允许超过
  - xfs_quota -x -c 'limit -u bsoft=5 bhard=10 <UserName>' </mnt/PartitonName> // 对数据块进行限制 软限制:在限定时间内允许超过一定的值 硬限制:不允许超过
- 磁盘的分区与挂载
  - 常用命令 // 保存在内存中 需要修改配置文件固化
    - fdisk + </dev/deviceName> // 输入 q 退出不保存 最后一步输入 w 保存并退出
    - mkfs<文件系统类型> + </dev/DeviceName>
    - parted + </dev/DeviceName> // 硬盘大于 2T 则不能用 fdisk 进行分区,得用 parted
    - mount <可选: -t ext4 或 auto> <分区 /dev/PartitionName> </mnt/PartitionName> // 将<分区 /dev/PartitionName>挂载到</mnt/PartitionName>
  - 常用配置文件
    - /etc/fstab
      - vim /etc/fstab
      - 添加 </dev/PartitionName> </mnt/PartitionName> ext4 defaults 0 0 // 保存后退出,以后系统开机后该分区就可以自动进行挂载了
- 交换分区(虚拟内存)的查看与创建
- 软件 RAID 的使用
  - RAID 的常见级别及含义
    - RAID 0 striping 条带方式, 提高单盘吞吐率
    - RAID 1 mirroning 镜像方式, 提高可靠性
    - RAID 5 有奇偶校验
    - RAID 10 是 RAID 1 与 RAID 0 的结合
    - mdadm -C </dev/RaidDeviceName> -a yes -l1 -n2 </dev/DeviceName1> </dev/DeviceName2> // -a 表示同意创建设备, -l 表示 raid 的级别, -n 表示活动的硬盘, </dev/DeviceName1> </dev/DeviceName2>也可用通配符写法 e.g. /dev/sd[b, c]1
    - mdadm -D </dev/RaidDeviceName>
    - dd if=/dev/zero of=</dev/DeviceName1> bs=4M count=1 // 破坏 </dev/DeviceName1> 同时 Raid 也会被破坏 可以通过软件 mdadm 或可以直接更换硬盘 因为支持热拔插
    - echo DEVICE /dev/sdp[b, c]1 >> /etc/mdadm.conf // 这样开机的时候软件才会被自动被加载
    - mdadm -Evs >> /etc/mdadm.conf // 把 raid 的属性追加到/etc/mdadm.conf 这样开机的时候软件才会被自动被加载
    - mdadm.xfs </dev/RaidDeviceName1> // 格式化
    - mdadm --stop </dev/RaidDeviceName> // 关闭 raid
    - dd if=/dev/zero of=</dev/DeviceName1> bs=1M count=1 // 破坏超级块
- 逻辑卷管理
  - 逻辑卷和文件系统的关系
  - 为 Linux 创建逻辑卷
    - pvcreate </dev/DeviceName1> </dev/DeviceName2> </dev/DeviceName3> 或 pvcreate </dev/sd[b, c, d]1>
    - pvs // 查看物理卷 PV:物理卷 VG:卷组
    - vgcreate <lvmGroupName> </dev/DeviceName> // 一个 PV 不能加入到两个卷组
    - vgs // 查看卷组
    - lvcreate -L <逻辑卷大小> -n </dev/lvmName> <lvmGroupName> // 创建逻辑卷大小
    - mkfs.xfs </dev/lvmGroupName/lvmName>
    - mount
  - 动态扩容逻辑卷
    - lvs 或 mount // 查看/root 及/ 在哪个分区
    - mount | grep root // 查看 root 在哪个分区
    - vgextend <lvmGroupName> </dev/DeviceName>
    - lvmextend -L +<扩充的大小> </dev/lvmGroupName/lvmName>
    - xfs_growfs </dev/lvmGroupName/lvmName> // 文件系统同步更新扩充后的逻辑卷容量大小
- 系统综合状态查看
  - 使用 sar 命令查看系统综合状态
    - sar -u <时间间隔> <采样次数> // 查看 cpu 运行情况
    - sar -r <时间间隔> <采样次数> // 查看内存读写情况
    - sar -d <时间间隔> <采样次数> // 查看磁盘读写情况
    - sar -p <时间间隔> <采样次数> // 查看进程情况
  - 使用第三方命令查看网络流量
    - yum install epel-release
    - yum install iftop
    - iftop -P // 观察网络情况 默认观察 eth0 的网络

### Bash

bash ./filename.sh // 不会改变当前工作环境 退出后即恢复 用子进程方式
./filename.sh // 不会改变当前工作环境 退出后即恢复 用子进程方式
source ./filename.sh // 会改变当前工作环境
. filename.sh // 会改变当前工作环境

### 打开终端环境变量加载过程

- su - <UserName>
  1. `/etc/profile`
  2. `.bash_profile`
  3. `.bashrc`
  4. `/etc/bashrc`
- su <UserName>
  1. `.bashrc`
  2. `/etc/bashrc`

### Java 环境变量设置(参考)

export JAVA_HOME=/usr/lib/jvm/jdk
export J2SDKDIR=/usr/lib/jvm/jdk
export DERBY_HOME=/usr/lib/jvm/jdk/db
export J2REDIR=/usr/lib/jvm/jdk
export PATH=$PATH:JAVA_HOME/bin
export PATH=$PATH:DERBY_HOME

### 防火墙

- 防火墙分类
  - 软件防火墙和硬件防火墙
  - 包过滤防火墙和应用层防火墙
    - CentOS 6 默认的防火墙是 iptables
    - CentOS 7 默认的防火墙 firewallD(底层使用 netfilter)
- iptables 的表和链
- iptables 的 fiter 表
- iptables 的 nat 表
- ipatables 配置文件
- firewallD 服务

### ssh

```bash
ssh-keygen -t rsa
ssh-copy-id  username@<ip_Adress>    // 将公钥拷贝进目标主机的authorized_keys
scp <filename> username@<ip_Adress>:</username/filename>    // 将本机<filename>拷贝到username@<ip_Adress>:</username/filename>
scp username@<ip_Adress>:<dir/filename> </username/filename>    // 将username@<ip_Adress>:<dir/filename>拷贝到本机</username/filename>
```
