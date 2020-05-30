---
title: 不翻墙快速下载CocoaPods索引的方法
date: 2020-05-30 17:57:16
tags: pod
---

## 起因

上个月换了工作，远程入职，然后领了新电脑，需要配置工作环境，但是你们懂得原因，网络不给力啊。

经过N次pod拉取失败后，终于是忍无可忍，只能曲线救国了。下面分享本人整理的操作步骤。



## 操作步骤

1. 通过镜像下载索引
2. 修改仓库的origin地址
3. 同步最新索引
4. 愉快的使用cocoapods



### 1. 通过镜像下载索引

对于旧版的 CocoaPods 可以使用如下方法使用 tuna 的镜像：

```
$ pod repo remove master
$ pod repo add master https://mirrors.tuna.tsinghua.edu.cn/git/CocoaPods/Specs.git
$ pod repo update
```



新版的 CocoaPods 不允许用`pod repo add`直接添加master库了，但是依然可以：

```
$ cd ~/.cocoapods/repos 
$ pod repo remove master
$ git clone https://mirrors.tuna.tsinghua.edu.cn/git/CocoaPods/Specs.git master
```



最后进入自己的工程，在自己工程的`Podfile`第一行加上：

```
source 'https://mirrors.tuna.tsinghua.edu.cn/git/CocoaPods/Specs.git'
```



### 2. 修改仓库的origin地址

通过镜像下载的索引，在工程中使用的时候，需要指定source，这样非常不友好，我们想办法把制定source这一步给干掉。

我们是通过git下载的索引，所以这些索引其实就是一个git仓库，我们把仓库的远端地址修改为GitHub上cocoapods的官方地址，那就可以咯～



镜像地址：https://mirrors.tuna.tsinghua.edu.cn/git/CocoaPods/Specs.git

官方地址：https://github.com/CocoaPods/Specs.git

远程仓库名称：origin



#### 方法一 通过命令直接修改远程地址

```
$ cd ~/.cocoapods/repos/master
$ git remote set-url origin https://github.com/CocoaPods/Specs.git
```



#### 方法二 通过命令先删除再添加远程仓库

```
$ cd ~/.cocoapods/repos/master
$ git remote rm origin
$ git remote add origin https://github.com/CocoaPods/Specs.git
```



#### 方法三 直接修改配置文件

```
$ cd ~/.cocoapods/repos/master/.git
$ vi config //把里面的url替换为https://github.com/CocoaPods/Specs.git
```



完整文件内容如下：

```
[core]
	repositoryformatversion = 0
	filemode = true
	bare = false
	logallrefupdates = true
	ignorecase = true
	precomposeunicode = true
[remote "origin"]
	url = https://github.com/CocoaPods/Specs.git
	fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
	remote = origin
	merge = refs/heads/master
```



#### 方法四 通过第三方git客户端修改

以SourceTree为例，点击 仓库 -> 仓库配置 -> 远程仓库 即可管理此项目中配置的所有远程仓库， 而且这个界面最下方还可以点击编辑配置文件，同样可以完成方法三。



### 3. 同步最新索引

清华的镜像索引是定期同步官方索引的，所以如果想要得到最新的索引，可以手动用命令拉取一次。

```
$ cd ~/.cocoapods/repos/master
$ git pull
```



### 4. 愉快的使用cocoapods

后面就是和官方安装的方式一样了



## 最后

### 杭州字节招人啊！！！！

### 杭州字节招人啊！！！！

### 杭州字节招人啊！！！！

### 内推走起，等着大伙简历啊

联系方式：

qq（微信）：410289616

email：emh1cnVob25nQGJ5dGVkYW5jZS5jb20=