#我们编程吧 之 Linux 学习手册
**Version 0.1 **

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



#更多信息
Hi，XDJM们，更多信息欢迎移步[我的github](https://github.com/shaoguangleo)或微信公众号letsProgramming.

![letsProgramming](http://img.blog.csdn.net/20160128231400788)
