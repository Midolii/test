# 个人Git食用文档

[url](https://github.com/Midolii/How-to-eat-Git "本文地址")

* 此文档为基础文档，不涉及分支的创建，切换以及合并
* 可能会有一些遗漏的地方
* 平台为windows，linux和mac平台配置相应过程基本没有区别

## 简介

>git是一个分布式版本控制软件，最初由Linux Tovalds(Linux之父)创作，于2005年发布。
>最初的目的是为了更好的管理Linux内核的开发。

## git的下载与安装

* 由于网络问题，为了方便，这里贴出我已经下载好并上传的2.27.0的64位windows版本  [Git-download](http://192.144.232.218:10031/#/s/p3I6 "Git")(链接地址为我自己搭建的网盘地址，网址是安全的，请放心访问)
* 安装时全部默认即可

## vscode的下载与安装

* vscode是微软开发的一款非常受欢迎的文本编辑器，里面可以下载各种插件来简化我们的开发流程，可以在里面快速进行git提交和拉取等操作。
* 为了方便，这里也贴出下载好并上传的1.47.0的64位windows版vscode。
* 安装时:

>将"通过code打开"操作添加到windows资源管理器文件上下文菜单
>将"通过code打开"操作添加到windows资源管理器目录上下文菜单
>将code注册为受支持的文件类型的编辑器

* 推荐勾选以上三项，以后编写代码或者提交代码会很方便。

* 推荐的主题:Nebula Theme

## github上相关的操作(远程库)

* [Github](https://github.com/ "Github")(Github官方页面)
* 上面为Github的地址，如果没有Github账户需要注册一个。
* 如果GitHub打开有困难，可以选择国内的coding和码云等代码托管平台。

* 创建好账户之后进入GitHub点击头像--your repositories--new。
* 库的名字是必填项，其他可以先忽略直接创建库。
* 进入库后选择ssh并记下右侧的类似于 "git@github.com:用户名/库名称" 的地址。

## bash中相关的操作

* 首先我们需要一个sshkey放到github的setting里面用来验证我们的身份。
* 如果在C/user/用户名/.ssh/下没有id_rsa和id_rsa.pub文件的话可以执行下面的命令，如果没有.ssh/ 这个文件夹的话，也需要执行下面的文件。

```bash
ssh-keygen -t rsa -C "你的邮箱"  #然后输入三次回车
```

* 之后在C/user/用户名/.ssh/ 这个目录下就会出现两个id_rsa开头的文件。
* 我们右键id_rsa.pub，选择使用vscode打开(或者其他编辑器)，将里面的内容全部复制。
* 然后打开我们的Github，点击头像--settings--ssh and gpg keys--new。
* title随便填写，只需要我们识别就可以，然后把刚才复制的粘贴到下面的key里面，然后点击add ssh key
* 回到bash  执行下面的命令

```bash
ssh -T git@github.com
```

* 出现Hi，"你的用户名"相关字样即密钥配队成功。

## git相关命令(本地库)

```bash
git init        #将当前所在文件夹转化为git仓库，文件夹里面会出现一个子文件夹.git 这个子文件夹是隐藏的，里面的相关文件用来记录当前库的信息。
git add 文件名      #将一个文件加入到工作队列中
git status      #查看当前队列中的文件
git commit -m "随便填写"        #将队列中的文件添加到本地库中(此处未进行推送步骤)，引号一定要有
##第一次推送需要执行下面两个命令
git remote add origin "github上创建好的库的ssh地址"     #将远程库的地址配置在本地库.git/config里， 不需要打引号
git push -u origin master       #将本地库推送到远程库(第一次推送)
##除第一次外之后的推送
git push        #第一次推送结束，以后直接git push即可
####################
git pull        #如果其他用户往远程库里面新增了文件，我们需要先拉取一下远程库的文件然后才能继续工作，如果不拉取的话推送会出错。
####################
git clone 随便一个库的地址      #克隆自己的库或者其他的库，克隆之后不需要配置remote add，然后推送直接输入 git push即可

git diff        #如果文件更改，则会显示更改的内容
.
.
.
```

## 在vscode使用git

* 右键一个本地库的文件夹选择使用vscode打开
* vscode左面列表第三个类似于一个分支的图标就是git的相关工具。
* 如果我们在当前的库有一个新的文件需要提交，那么在点击这个图标就会看到change一栏下面会出现相应的文件
* 点击一下加号(git add)，然后再点击一下上面的对号(git commit -m)之后会弹出一个框，这个框里面输入的东西就是git commit -m "引号里面的东西"，至此我们提交到本地库成功。
* 然后点击对号最右面那个省略号，下面有一个push(git push)，即可把本地库文件推送到远程库(相应的，里面也有git的其他操作，比如说pull之类的)
