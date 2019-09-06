---
title: 配置SSH密钥
date: 2019-09-06 11:20:28
tags: 
- hexo
- SSH
---


## 配置SSH密钥

* 1.确认是否存在SSH密钥

> 终端执行 cd ~/.ssh/
> 检查你本机用户home目录下是否存在.ssh目录

> 如果，不存在此目录，则进行第二步操作，否则，你本机已经存在ssh公钥和私钥，可以略过第二步，直接进入第三步操作。


* 2.创建一对新的SSH密钥

> $ssh-keygen -t rsa -C "your_email@example.com" **这将按照你提供的邮箱地址，创建一对密钥**

> Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/you/.ssh/id_rsa): [Press enter]
>
> 直接回车，则将密钥按默认文件进行存储。此时也可以输入特定的文件名，比如/c/Users/you/.ssh/github_rsa
>
> 接着，根据提示，你需要输入密码和确认密码（说到这里，如果你很放心，其实可以不用密码，就是到输密码的地方，都直接回车，所以每次push就只管回车就行了。所谓的最安全的密码，就是没有密码 哈哈）。相关提示如下：
>
> Enter passphrase (empty for no passphrase): [Type a passphrase]
Enter same passphrase again: [Type passphrase again]
输入完成之后，屏幕会显示如下信息：
>
> Your identification has been saved in /c/Users/you/.ssh/id_rsa.
Your public key has been saved in /c/Users/you/.ssh/id_rsa.pub.
The key fingerprint is:
01:0f:f4:3b:ca:85:d6:17:a1:7d:f0:68:9d:f0:a2:db your_email@example.com


* 3.在github账户中添加你的公钥

> 查看公钥命令：cat ~/.ssh/id_rsa.pub 
> 
> 登陆GitHub,进入你的Account Settings.
> 
> 选择SSH Keys，粘贴密钥，添加即可


* 4.测试设置是否成功

> 使用命令：$ ssh -T git@github.com

```
192:~ zhuruhong$ ssh -T git@github.com
The authenticity of host 'github.com (52.74.223.119)' can't be established.
RSA key fingerprint is SHA256:xxxxxxxx.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added 'github.com,52.74.223.119' (RSA) to the list of known hosts.
Hi zhu410289616! You've successfully authenticated, but GitHub does not provide shell access.
192:~ zhuruhong$ 
```

* 5.设置用户信息

> 现在你已经可以通过SSH链接到GitHub了，还有一些个人信息需要完善的。 Git会根据用户的名字和邮箱来记录提交。GitHub也是用这些信息来做权限的处理，输入下面的代码进行个人信息的设置，把名称和邮箱替换成你自己的，名字根据自己的喜好自己取，而不是GitHub的昵称。

```
$ git config --global user.name "zhu410289616"//用户名
$ git config --global user.email  "zhu410289616@163.com"//填写自己的邮箱
```

* 6.SSH Key配置成功
