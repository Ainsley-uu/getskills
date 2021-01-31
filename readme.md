## 创建空目录

```makefile
$ mkdir learngit
$ cd learngit
$ pwd
/Users/michael/learngit
```

## 把目录变成Git可以管理的仓库

```makefile
$ git init
```

没有看到`.git`目录，因为这个目录是隐藏的，用`ls -ah`命令可以看见

可以选择一个已经有东西的目录也是可以的

## 把文件添加到版本库

编写一个`readme.txt`文件，内容如下：

```makefile
Git is a version control system.
Git is free software.
```

+ 用命令`git add`告诉Git，把文件添加到仓库：

```makefile
$ git add readme.txt
```

