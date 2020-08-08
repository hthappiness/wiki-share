# git

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## 基本概念

工作区，版本库；

工作区有一个隐藏目录`.git`，这个不算工作区，而是Git的版本库。

Git的版本库里存了很多东西，其中最重要的就是称为stage（或者叫index）的暂存区，还有Git为我们自动创建的第一个分支`master`，以及指向`master`的一个指针叫`HEAD`。具体如下图所示

![](https://www.liaoxuefeng.com/files/attachments/919020037470528/0)

## git原理

这是一个文件数据库，记录修改文件的各种版本记录

sha256

## Commands

根据git的内部组成，且看每一个命令执行背后的操作

* `git init [dir-name]` - Create a new project.
* `git add` - Start the live-reloading docs server.
* `git commit` - Build the documentation site.
* `git push` - Print help message and exit.
* `git pull`
* `git fetch`
* `git rebase`
* `git merge`
* `git revert`
* `git stage`
* `git status`
* `git branch`
* `git tag`
* `git rm`，
  * `git rm` ： 同时从工作区和索引中删除文件。即本地的文件也被删除了。
  * `git rm --cached filename` ： 从索引中删除文件,操作的是版本库而不是工作区。但是本地文件还存在， 只是不希望这个文件被版本控制。

## 常见问题

### 过滤条件用.gitignore文件

在git提交commit的时候回忽略掉gitignore中包含的文件

文件编写方式

```
#这是相对路径
*.a       # 忽略所有 .a 结尾的文件
!lib.a    # 但 lib.a 除外
/TODO     # 仅仅忽略项目根目录下的 TODO 文件，不包括 subdir/TODO
build/    # 忽略 build/ 目录下的所有文件
doc/*.txt # 会忽略 doc/notes.txt 但不包括 doc/server/arch.txt
```

#### gitignoreglobal

另外 git 提供了一个全局的 .gitignore，你可以在你的用户目录下创建 ~/.gitignoreglobal 文件，以同样的规则来划定哪些文件是不需要版本控制的。

需要执行 git config --global core.excludesfile ~/.gitignoreglobal来使得它生效。

其他的一些过滤条件

```
  \* ？：代表任意的一个字符
  \* ＊：代表任意数目的字符
  \* {!ab}：必须不是此类型
  \* {ab,bb,cx}：代表ab,bb,cx中任一类型即可
  \* [abc]：代表a,b,c中任一字符即可

  \* [ ^abc]：代表必须不是a,b,c中任一字符
```

  由于git不会加入空目录，所以下面做法会导致tmp不会存在 tmp/*       //忽略tmp文件夹所有文件

  改下方法，在tmp下也加一个.gitignore,内容为

```
*
!.gitignore  
```

  还有一种情况，就是已经commit了，再加入gitignore是无效的，所以需要删除下缓存 

```shell
git rm -r --cached ignore_file
```

 

注意： .gitignore只能忽略那些原来没有被track的文件，如果某些文件已经被纳入了版本管理中，则修改.gitignore是无效的。

 正确的做法是在每个clone下来的仓库中手动设置不要检查特定文件的更改情况。

```shell
git update-index --assume-unchanged PATH  #在PATH处输入要忽略的文件。
```

  另外 git 还提供了另一种 exclude 的方式来做同样的事情，不同的是 .gitignore 这个文件本身会提交到版本库中去。用来保存的是公共的需要排除的文件。而 .git/info/exclude 这里设置的则是你自己本地需要排除的文件。 他不会影响到其他人。也不会提交到版本库中去。

  .gitignore 还有个有意思的小功能， 一个空的 .gitignore 文件 可以当作是一个 placeholder 。当你需要为项目创建一个空的 log 目录时， 这就变的很有用。 你可以创建一个 log 目录 在里面放置一个空的 .gitignore 文件。这样当你 clone 这个 repo 的时候 git 会自动的创建好一个空的 log 目录了。



但是有时候，gitignore考虑不全面，发现有不该提交的文件已经提交后，仅仅在.gitignore中加入忽略是不行的。这个时候需要执行:

```shell
git rm -r --cached filename 
```

去掉已经托管的文件，然后提交即可

### 如何建立一个本地仓库

在github之上创建一个github地址`https://github.com/hthappiness/wiki-share.git`，然后进入要建立git记录的文件夹下执行如下命令：

```shell
 git init
 git remote add origin https://github.com/hthappiness/wiki-share.git
 git add . 
 git commit -m "init wiki"
 git push -u origin master
```



## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.



## other

1. github
2. gitlab

## 参考资料