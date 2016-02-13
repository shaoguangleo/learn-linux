#我们编程吧 之 Linux 学习手册
**Version 0.3 **

[TOC]

##diff  比较两个目录的不同
diff命令会按行比较文件。但是它也可以比较两个目录：

 1. ls -l /tmp/r
 2. ls -l /tmp/s
 3. 使用 diff 比较两个文件夹
 4. diff /tmp/r/ /tmp/s/

##锁定Linux文件夹

为了我的数据隐私，我想要锁定我文件服务器下的/downloads文件夹。因此我运行了：

```
chmod 0000 /downloads
```

root用户仍旧可以访问，而ls和cd命令则不工作。要还原它用：

```
chmod 0755 /downloads
```



##tee可以看见输出并将其写入到一个文件中

可以看见输出并将其写入到一个文件中

如下使用tee命令在屏幕上看见输出并同样写入到日志文件my.log中

```
ls | tee my.log
```

tee可以保证你同时在屏幕上看到ls的输出并写入文件  my.log。

tee 的解释为：*read from standard input and write to standard output and files*

##如何用cp拷贝指定序号的文件

现在有文件夹filename，内有文档，名字是从1.dat, 2.dat, 3.dat 一直到9999.dat,10000.dat,现在希望从第N组数据即N.dat到第M组数据M.dat的文件拷贝到别的文件夹中，方法如下：

```
cp {N..M}.dat   newfilename/
```

这个方法可是相当的赞呀~\(≧▽≦)/~


##cd的妙用

想要进入刚才进入的地方？运行：

cd –

需要快速地回到你的家目录？输入：这里其实不用一级一级的进入

cd

变量CDPATH定义了目录的搜索路径：

```
export CDPATH=/var/www:/nas10
```

现在，不用输入`cd */var/www/html/` 这样长了，我可以直接输入下面的命令进入 /var/www/html：

```
cd html
```

```
cd ~username
```
进入username的家目录。

##chmod

Linux/Unix 的档案存取权限分为三级 : 档案拥有者、群组、其他。利用 chmod 可以控制档案如何被他人所存取。


mode : 权限设定字串，格式如下 : [ugoa…][[+-=][rwxX]…][,…]

其中u 表示该档案的拥有者，g 表示与该档案的拥有者属于同一个群体(group)者，o 表示其他以外的人，a 表示这三者皆是。

`+` 表示增加权限、– 表示取消权限、= 表示唯一设定权限。

r 表示可读取，w 表示可写入，x 表示可执行，X 表示只有当该档案是个子目录或者该档案已经被设定过为可执行。

-c : 若该档案权限确实已经更改，才显示其更改动作

-f : 若该档案权限无法被更改也不要显示错误讯息

-v : 显示权限变更的详细资料

-R : 对目前目录下的所有档案与子目录进行相同的权限变更(即以递回的方式逐个变更)

```
若用chmod 4755 filename可使此程式具有root的权限
```


##find命令
find命令是一个在UNIX文件系统中查找文件的常用命令，可以进行很多条件查找。

find的语法: `find 路径 约束条件`

如何查找在文件名中含有指定关键字的文件呢？

下面这条命令查找在“/etc”目录下所有文件名中含有“mail”的find /etc -name “*mail*”找在最近几天没有被修改过的文件？

下面这条命令会列出在当前目录下在最近60天没有被修改过文件

 `find . -mtime +60`

如何查找在最近几天被修改的文件？

下面这条命令会列出在当前目录下在最近2天被修改过文件

```
find . –mtime -2
```


#更多信息
Hi，XDJM们，更多信息欢迎移步[我的github](https://github.com/shaoguangleo)或微信公众号letsProgramming.

![letsProgramming](http://img.blog.csdn.net/20160128231400788)
