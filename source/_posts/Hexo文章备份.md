---
title: Hexo文章备份
date: 2019-09-06 14:20:00
tags: hexo
---

## Hexo文章备份

* 1.利用分支分开保存网站资源和写作文件

> Hexo 的部署默认使用 **master** 分支，创建写作分支 **hexo**，我把写作分支命名为hexo。
> 
> 先切换到master分支的publish目录下，执行如下命令：

```
git init
git remote add origin https://github.com/zhu410289616/zhu410289616.github.io.git
git add .
git commit -m "xxxx，这里是提交记录的描述"
git push -f origin master:hexo
```


* 2.修改发布目录中的_config.xml文件，添加hexo的备份配置

> 发布分支配置

```
deploy:
  type: git
  repo: https://github.com/zhu410289616/zhu410289616.github.io.git
  branch: master
```

> 备份分支配置

```
backup:
    type: git
    message: update for hexo blog website
    repository:
       github: git@github.com:zhu410289616/zhu410289616.github.io.git
       branch: hexo
```

* 3.提交备份

> 以后执行发布命令后 **hexo g -d**，执行备份命令 **hexo b**，就可以备份到github仓库中了