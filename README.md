# How-to-add-my-Repositories

关于如何管理、使用、存储、公共库。

首先基础的命令使用需要有第一印象，也就是如何创建初始文件，提交更改的文件。

git 其实是一个本地仓库，可以通过 `push` 指令把数据同步到 GitHub（远程仓库）上。

而本地仓库由两部分构成：

1. 可见的工作区（Working Directory），即我们本地的文件；
2. 不可见的版本库（Repository），包括两个部分：
   - 暂存区（Stage）
   - 本地分支（branch）

要成功将本地文件 `push` 到 GitHub，至少需要三个步骤：

1. 通过 `git add` 将文件从工作区添加到暂存区；
2. 通过 `git commit` 将文件从暂存区提交到本地分支；
3. 通过 `git push` 将文件从本地分支推送到远程仓库。

使用下面的命令，进入本地存储库，然后提交所有的文件到暂存区域，暂存之后就可以提交更改了。

```shell
cd username.github.io
git add .
git commit -a -m "msg"
git push origin main
```

注意第3行命令-m代表要添加的本次提交代码注释信息，如果不加上双引号内容，会自动进入一个文件，手动填写很麻烦，要避免。如下信息表示提交成功到main分支。

![image-20240116033608392](https://githubwiki.oss-cn-shanghai.aliyuncs.com/img/typroa/image-20240116033608392.png)

打开网页链接：https://github.com/TangerineSec/How-to-add-my-Repositories，可以看到当前提交的内容与网页内容已经成功同步。

![image-20240116033814124](https://githubwiki.oss-cn-shanghai.aliyuncs.com/img/typroa/image-20240116033814124.png)

## 如何在父目录下连续执行这几条重复命令并且执行呢？

首先使用cd命令进入上一级目录，将这个文本文件存储在目录下：

```shell
#!/bin/sh
echo "what is your name?"
read name
echo "How do you do, $name?"
read remark
echo "I am $remark too!"
```

使用./gitpush，执行这个文本文件，第一行脚本会切换到sh命令，使得下面的命令可以执行。执行结果如下：

![image-20240116035043087](https://githubwiki.oss-cn-shanghai.aliyuncs.com/img/typroa/image-20240116035043087.png)

所以，类似的，可以前面的3个提交命令组合，加上一个进入目录的命令，执行如下命令：

```shell
#!/bin/sh
cd /w/GitStore
git add .
git commit -a -m "commit message"
git push origin main
```

添加echo命令，输出更加人性化一点。我写入如下文本内容，可以一键执行，得到的结果如下。

```
#!/bin/sh
cd /w/GitStore
git add .
git commit -a -m "commit message"
git push origin main
echo "提交完毕，开始推送，已经完成。"
```

![image-20240116040009642](https://githubwiki.oss-cn-shanghai.aliyuncs.com/img/typroa/image-20240116040009642.png)

这样，下次再更改本地文件夹的内容时，就可以很快速流畅地进行提交所有内容了。
