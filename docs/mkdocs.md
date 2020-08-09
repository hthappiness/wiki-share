# MkDocs

For full documentation visit [mkdocs.org](https://www.mkdocs.org).

## Commands

* `mkdocs new [dir-name]` - Create a new project.在某个目录下创建一个新的工程，创建完之后，会有一个mkdocs.yml和docs文件夹
  * docs文件夹下存放的就是自己写的Markdown文章，系统默认会生成一个index.md文件
  * mkdocs.yml是wiki网站的配置文件（主题、目录、语言等）
  * 在docs目录下创建文件夹，作为markdown的相对路径使用，所有数据存储在github服务器上
* `mkdocs serve` - Start the live-reloading docs server.在本地启动网页服务器
* `mkdocs build` - Build the documentation site. 构建网页
* `mkdocs -h` - Print help message and exit.
* `mkdocs gh-deploy`，这是mkdocs的部署，完成的功能就是根据mkdocs.yml生成网页，然后建立分支，推送该网页

## mkdocs安装

在windows和linux上都是使用python安装

[mkdocs安装]: https://www.mkdocs.org/#installation

## mkdocs主题

使用pip安装主题

```shell
pip install mkdocs-material
```

在mkdocs.yml中修改主题

```
theme:
  name: 'material'
```

之后就是部署站点

```shell
mkdocs gh-deploy
```

其它

这是主题设置的[参考]（https://www.jianshu.com/p/c005c45abe85）

## mkdocs与github联动

> 使用mkdocs gh-deploy


## FAQ

1、pip安装超时的问题

pip和pip3的区别

pip是python installation package的abbreviation， python三方包管理工具

mkdocs的依赖项

2、其它wiki

[confluence]: https://blog.csdn.net/m0_37499059/article/details/81220649
[amwiki]: http://amwiki.org/doc/

