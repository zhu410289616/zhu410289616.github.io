---
title: 安装Hexo
date: 2019-09-06 11:19:46
tags: hexo
---

## 安装Hexo

* 1.Hexo安装文档：[https://hexo.io/zh-cn/docs/](https://hexo.io/zh-cn/docs/)


* 2.安装Hexo：**npm install -g hexo-cli**

```
192:RHSocketKit zhuruhong$ npm install -g hexo-cli
/usr/local/bin/hexo -> /usr/local/lib/node_modules/hexo-cli/bin/hexo

> fsevents@1.2.9 install /usr/local/lib/node_modules/hexo-cli/node_modules/fsevents
> node install

node-pre-gyp WARN Using needle for node-pre-gyp https download 
[fsevents] Success: "/usr/local/lib/node_modules/hexo-cli/node_modules/fsevents/lib/binding/Release/node-v67-darwin-x64/fse.node" is installed via remote
+ hexo-cli@2.0.0
added 255 packages from 458 contributors in 89.706s
192:RHSocketKit zhuruhong$ 
```

* 3.同时安装 hexo-deployer-git：**npm install hexo-deployer-git --save**

```

```

* 4.创建项目文件存放目录：如 **～/Desktop/hexo/github/**

```
192:~ zhuruhong$ cd ~/Desktop/hexo/github
192:github zhuruhong$ 
192:github zhuruhong$ pwd
/Users/zhuruhong/Desktop/hexo/github
192:github zhuruhong$ 
```

* 5.初始化博客项目：**hexo init**

```
192:github zhuruhong$ hexo init
INFO  Cloning hexo-starter https://github.com/hexojs/hexo-starter.git
Cloning into '/Users/zhuruhong/Desktop/hexo/github'...
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 81 (delta 0), reused 1 (delta 0), pack-reused 77
Unpacking objects: 100% (81/81), done.
Submodule 'themes/landscape' (https://github.com/hexojs/hexo-theme-landscape.git) registered for path 'themes/landscape'
Cloning into '/Users/zhuruhong/Desktop/hexo/github/themes/landscape'...
remote: Enumerating objects: 1018, done.        
remote: Total 1018 (delta 0), reused 0 (delta 0), pack-reused 1018
Receiving objects: 100% (1018/1018), 3.20 MiB | 4.00 KiB/s, done.
Resolving deltas: 100% (555/555), done.
Submodule path 'themes/landscape': checked out '73a23c51f8487cfcd7c6deec96ccc7543960d350'
INFO  Install dependencies
npm WARN deprecated core-js@1.2.7: core-js@<2.6.8 is no longer maintained. Please, upgrade to core-js@3 or at least to actual version of core-js@2.

> fsevents@1.2.9 install /Users/zhuruhong/Desktop/hexo/github/node_modules/fsevents
> node install

node-pre-gyp WARN Using needle for node-pre-gyp https download 
[fsevents] Success: "/Users/zhuruhong/Desktop/hexo/github/node_modules/fsevents/lib/binding/Release/node-v67-darwin-x64/fse.node" is installed via remote
npm notice created a lockfile as package-lock.json. You should commit this file.
added 421 packages from 524 contributors and audited 6890 packages in 52.479s
found 1 low severity vulnerability
  run `npm audit fix` to fix them, or `npm audit` for details
INFO  Start blogging with Hexo!
192:github zhuruhong$ 
```

* 6.完成后，当前目录下生成一套标准的Hexo博客项目模版

> 实际发布时需要根据这套“源代码”当中的配置文件、博客文档（.md文件）、主题模板等，进行组合构建，生成服务器可识别的标准HTML网站目录

```
192:github zhuruhong$ pwd
/Users/zhuruhong/Desktop/hexo/github
192:github zhuruhong$ 
192:github zhuruhong$ ls
_config.yml		package-lock.json	scaffolds		themes
node_modules		package.json		source
192:github zhuruhong$
```

* 7.生成网站：**hexo g**

> 执行完毕后，在public目录下可看到我们自己书写的博客文档（.md文件）与所选的博客主题模板链接组合，生成的最终静态网站文件，该目录也差不多就是之后发布到GitHub上的实际文件（实际发布到GitHub的是.deploy_git目录），外部的网站“源代码”不会上传到github.io库

```
192:github zhuruhong$ hexo g
INFO  Start processing
INFO  Files loaded in 352 ms
INFO  Generated: index.html
INFO  Generated: archives/index.html
INFO  Generated: fancybox/blank.gif
INFO  Generated: fancybox/fancybox_loading.gif
INFO  Generated: fancybox/fancybox_loading@2x.gif
INFO  Generated: fancybox/fancybox_overlay.png
INFO  Generated: fancybox/fancybox_sprite.png
INFO  Generated: fancybox/fancybox_sprite@2x.png
INFO  Generated: archives/2019/09/index.html
INFO  Generated: js/script.js
INFO  Generated: fancybox/helpers/jquery.fancybox-buttons.js
INFO  Generated: fancybox/jquery.fancybox.pack.js
INFO  Generated: fancybox/jquery.fancybox.css
INFO  Generated: fancybox/helpers/jquery.fancybox-media.js
INFO  Generated: css/style.css
INFO  Generated: fancybox/helpers/jquery.fancybox-buttons.css
INFO  Generated: archives/2019/index.html
INFO  Generated: fancybox/helpers/jquery.fancybox-thumbs.js
INFO  Generated: fancybox/helpers/jquery.fancybox-thumbs.css
INFO  Generated: css/fonts/fontawesome-webfont.woff
INFO  Generated: fancybox/helpers/fancybox_buttons.png
INFO  Generated: css/fonts/FontAwesome.otf
INFO  Generated: css/fonts/fontawesome-webfont.eot
INFO  Generated: css/fonts/fontawesome-webfont.ttf
INFO  Generated: css/fonts/fontawesome-webfont.svg
INFO  Generated: 2019/09/05/hello-world/index.html
INFO  Generated: fancybox/jquery.fancybox.js
INFO  Generated: css/images/banner.jpg
INFO  28 files generated in 922 ms
192:github zhuruhong$ 
```

* 8.启动本地服务器：**hexo s**

> 启动本地服务器可即时查看网站运行效果。默认地址是：localhost:4000

```
192:github zhuruhong$ hexo s
INFO  Start processing
INFO  Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.
```

* 9.选择主题

> Hexo可随时使用、更换博客主题
>
> 主题文件可在[Hexo官方主题网页](https://hexo.io/themes/) [https://hexo.io/themes/](https://hexo.io/themes/) 中下载，以Material为例，点击主题预览图下方的主题名称链接即可进入该主题的源码发布页面 [GitHub - viosey/hexo-theme-material: Material Design theme for hexo](https://github.com/viosey/hexo-theme-material).
> 
>
> 根据主题安装指导，下载项目至博客项目下的<mark>themes</mark>目录中，文件夹命名为<mark>material</mark>，并在博客配置文件<mark>_config.yml</mark>中指定使用该主题：
>
> **theme: material**
> 
> 将material主题目录下的<mark> _config.template.yaml</mark> 重命名为<mark> _config.yaml</mark>
>
> 参考[Material主题文档](https://material.viosey.com/docs/#/)进行必要配置
>
> 再次执行 hexo g 将会根据新主题重新构建整个博客

```
192:github zhuruhong$ npm i hexo-generator-json-content --save && npm i --save hexo-wordcount && git clone https://github.com/fi3ework/hexo-theme-archer.git themes/archer --depth=1
+ hexo-generator-json-content@4.1.6
added 13 packages from 28 contributors and audited 6914 packages in 23.325s
found 1 low severity vulnerability
  run `npm audit fix` to fix them, or `npm audit` for details
+ hexo-wordcount@6.0.1
added 1 package from 1 contributor and audited 6915 packages in 10.339s
found 1 low severity vulnerability
  run `npm audit fix` to fix them, or `npm audit` for details
Cloning into 'themes/archer'...
remote: Enumerating objects: 134, done.
remote: Counting objects: 100% (134/134), done.
remote: Compressing objects: 100% (124/124), done.
remote: Total 134 (delta 1), reused 88 (delta 0), pack-reused 0
Receiving objects: 100% (134/134), 1.67 MiB | 4.00 KiB/s, done.
Resolving deltas: 100% (1/1), done.
192:github zhuruhong$
```

```
> 修改 ~/Desktop/hexo/github 目录下的_config.yml的theme字段为archer

theme: archer
```

* 10.创建github.io仓库

> 在自己的GitHub中，创建新仓库，标准命名为GitHub用户名.github.io，例如我的：zhu41029616.github.io
> 
> 仓库Readme、License之类的留空即可，之后在发布上传时会被强制覆盖抹掉

* 11.配置SSH密钥

> 配置Github的SSH密钥可以让本地git项目与远程的github建立联系，让我们在本地写了代码之后直接通过git操作就可以实现本地代码库与Github代码库同步。
> 参考[SSH密钥配置]() []()

* 12.修改博客配置文件：**_config.yml**

```
deploy:
  type: git
  repo: GitHub上传仓库的完整路径，如 https://github.com/zhu410289616/zhu410289616.github.io.git
  branch: master
```

* 13.发布博客到github

> 在hexo g生成完毕后，可执行该命令发布博客到GitHub上：hexo d
> 
> 或在生成网站的同时进行发布： hexo g -d

```
192:github zhuruhong$ npm install --save hexo-deployer-git
+ hexo-deployer-git@2.0.0
added 19 packages from 22 contributors and audited 6992 packages in 14.964s
found 1 low severity vulnerability
  run `npm audit fix` to fix them, or `npm audit` for details
192:github zhuruhong$ 
192:github zhuruhong$ 
192:github zhuruhong$ hexo g -d
INFO  Start processing
INFO  Files loaded in 292 ms
hexo,hexo-theme,hexo-blog
hexo,hexo-theme,hexo-blog
hexo,hexo-theme,hexo-blog
hexo,hexo-theme,hexo-blog
hexo,hexo-theme,hexo-blog
INFO  0 files generated in 352 ms
INFO  Deploying: git
INFO  Setting up Git deployment...
Initialized empty Git repository in /Users/zhuruhong/Desktop/hexo/github/.deploy_git/.git/
[master (root-commit) 7430af3] First commit
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 placeholder
INFO  Clearing .deploy_git folder...
INFO  Copying files from public folder...
INFO  Copying files from extend dirs...
[master 37ab582] Site updated: 2019-09-06 09:35:01
 50 files changed, 6708 insertions(+)
 create mode 100644 2019/09/05/hello-world/index.html
 create mode 100644 archives/2019/09/index.html
 create mode 100644 archives/2019/index.html
 create mode 100644 archives/index.html
 create mode 100644 assets/algolia_logo.svg
 create mode 100644 assets/example_qr.png
 create mode 100644 assets/favicon.ico
 create mode 100644 assets/loading.svg
 create mode 100644 avatar/Misaka.jpg
 create mode 100644 content.json
 create mode 100644 css/fonts/FontAwesome.otf
 create mode 100644 css/fonts/fontawesome-webfont.eot
 create mode 100644 css/fonts/fontawesome-webfont.svg
 create mode 100644 css/fonts/fontawesome-webfont.ttf
 create mode 100644 css/fonts/fontawesome-webfont.woff
 create mode 100644 css/images/banner.jpg
 create mode 100644 css/mobile.css
 create mode 100644 css/style.css
 create mode 100644 fancybox/blank.gif
 create mode 100644 fancybox/fancybox_loading.gif
 create mode 100644 fancybox/fancybox_loading@2x.gif
 create mode 100644 fancybox/fancybox_overlay.png
 create mode 100644 fancybox/fancybox_sprite.png
 create mode 100644 fancybox/fancybox_sprite@2x.png
 create mode 100644 fancybox/helpers/fancybox_buttons.png
 create mode 100644 fancybox/helpers/jquery.fancybox-buttons.css
 create mode 100644 fancybox/helpers/jquery.fancybox-buttons.js
 create mode 100644 fancybox/helpers/jquery.fancybox-media.js
 create mode 100644 fancybox/helpers/jquery.fancybox-thumbs.css
 create mode 100644 fancybox/helpers/jquery.fancybox-thumbs.js
 create mode 100644 fancybox/jquery.fancybox.css
 create mode 100644 fancybox/jquery.fancybox.js
 create mode 100644 fancybox/jquery.fancybox.pack.js
 create mode 100644 font/Oswald-Regular.ttf
 create mode 100644 font/Source Sans Pro.woff
 create mode 100644 font/Source Sans Pro.woff2
 create mode 100644 font/SourceCodePro-Regular.ttf.woff
 create mode 100644 font/SourceCodePro-Regular.ttf.woff2
 create mode 100644 index.html
 create mode 100644 intro/404-bg.jpg
 create mode 100644 intro/about-bg.jpg
 create mode 100644 intro/index-bg.jpg
 create mode 100644 intro/post-bg.jpg
 create mode 100644 js/script.js
 create mode 100644 lib/jquery.min.js
 create mode 100644 lib/webfontloader.min.js
 delete mode 100644 placeholder
 create mode 100644 scripts/main.js
 create mode 100644 scripts/search.js
 create mode 100644 scripts/share.js
Counting objects: 71, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (60/60), done.
Writing objects: 100% (71/71), 1.70 MiB | 675.00 KiB/s, done.
Total 71 (delta 3), reused 0 (delta 0)
remote: Resolving deltas: 100% (3/3), done.
To https://github.com/zhu410289616/zhu410289616.github.io.git
 + 46a9699...37ab582 HEAD -> master (forced update)
Branch 'master' set up to track remote branch 'master' from 'https://github.com/zhu410289616/zhu410289616.github.io.git'.
INFO  Deploy done: git
192:github zhuruhong$ 
```

* 13.查看效果

> [https://zhu410289616.github.io/](https://zhu410289616.github.io/)

* 14.绑定域名

> 默认提供的是 GitHub用户名.github.io（例如我的：zhu410289616.github.io）作为博客访问地址，可设置绑定自定义域名
>
> 在博客项目目录的source文件夹中，创建一个CNAME文件，存储预备使用的个人域名，如：
>
> echo story.wavky.com > CNAME

>清理Hexo缓存并重新生成发布
>
> hexo clean
> 
> hexo g -d

