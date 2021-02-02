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
$ git add readme.md
```

+ 用命令`git commit`告诉Git，把文件提交到仓库：

```makefile
$ git commit -m "wrote a readme file"
```

简单解释一下`git commit`命令，`-m`后面输入的是本次提交的说明，可以输入任意内容，当然最好是有意义的，这样你就能从历史记录里方便地找到改动记录。

`git commit`命令执行成功后会告诉你，`1 file changed`：1个文件被改动（`readme.md文件`）；`2 insertions`：插入了两行内容（`readme.md`有两行内容）。

**注释：**

`commit`可以一次提交很多文件，所以你可以多次`add`不同的文件，比如：

```makefile
$ git add file1.txt
$ git add file2.txt file3.txt
$ git commit -m "add 3 files."
```

## 查看结果

```makefile
git status
```

虽然Git告诉我们`readme.md`被修改了，但如果能看看具体修改了什么内容，自然是很好的。比如你休假两周从国外回来，第一天上班时，已经记不清上次怎么修改的`readme.md`，所以，需要用`git diff`这个命令看看：

```makefile
git diff readme.md
```

同样没有任何输出。在执行第二步`git commit`之前，我们再运行`git status`看看当前仓库的状态

## 版本回退

在Git中，我们用`git log`命令查看历史记录：

```makefile
git log
```

Git必须知道当前版本是哪个版本，在Git中，用`HEAD`表示当前版本，也就是最新的提交`1094adb...`（注意我的提交ID和你的肯定不一样），上一个版本就是`HEAD^`，上上一个版本就是`HEAD^^`，当然往上100个版本写100个`^`比较容易数不过来，所以写成`HEAD~100`

```makefile
$ git reset --hard HEAD^
```

## 管理修改

```makefile
$ git add readme.md
$ git status
$ git commint -m "git tracks changes"
```

## Fork a repo

```
git clone 完整地址
```

---

### Push

**初始化**

```
git init
```

**加载文件**

```
git add .		# 所有文件
git add index.html,test.html	#单个文件
```

**提交文件**

```
git commit -m "init commit"
```

**查看git状态**

```
git status
```

**推送代码**

```
git push origin master
```

****

### 提交自己本地项目的修改到 github 的库中.

如果你自己的项目，你自己 clone 到本地后, 进行了一系列的修改， 然后你想提交， 大多最方便的方式是使用 HTTP 的方式进行提交。

但你提交的时候， 会发现一直提示：

```
error: The requested URL returned error: 403 Forbidden while accessing http://xxx
```

这时， 你需要修改你的项目目录下的 .git/config 文件 在 url 中修改成象

```
url = https://iakuf@github.com/iakuf/mojo
```

也就是给你的 github 的帐号名使用 @ 加到前面， 才能做为 HTTP 认证的用户来认证. 这样就不用关心 SSH 的 Key 的问题了。

### 更新自己 Fork 的代码项目和原作者的项目进度一致的方法

经过一段时间， 有可能作者原来的代码变化很大， 你想接着在他最新的代码上修改， 这时你需要合并原作者的最新代码过来， 让你的项目变成最新的。这个需要本地操作。 假设前提是， 你现在你的代码是克隆下来在本地的。 例如我 Fork 了 sri (Mojo 的作者) 的 Mojo 项目， 我的项目地址是 https://github.com/iakuf/mojo. 我现在克隆这个在我的本地了。

```
git clone https://github.com/iakuf/mojo
 cd mojo
```

接着， 我只需要添加 sri 项目的地址,也就是主项目的 remote 地址

```
git remote add sri https://github.com/kraih/mojo
git fetch sri
git merge sri/master
```

这新就能给你的本地的项目变成和主项目一样。 然后你按正常的流程进行修改并提交到你的项目就好了。

```
git commit -am '更新到原作者的主分支的进度'
git push origin
```