---
title: npm镜像源管理
date: 2019-09-28 10:27:35
tags: 
- hexo
- node
---

## npm镜像源管理

**常见npm命令记录:**

* 1. 查看npm源地址

```
192:Pipeline-Node zhuruhong$ npm config list
; cli configs
metrics-registry = "https://registry.npmjs.org/"
scope = ""
user-agent = "npm/6.4.1 node/v11.1.0 darwin x64"

; builtin config undefined
prefix = "/usr/local"

; node bin location = /usr/local/Cellar/node/11.1.0/bin/node
; cwd = /Users/zhuruhong/Desktop/pig/Pipeline-Node
; HOME = /Users/zhuruhong
; "npm config ls -l" to show all defaults.

192:Pipeline-Node zhuruhong$
```


* 2. 修改registry地址，比如修改为淘宝镜像源

```
npm set registry https://registry.npm.taobao.org/
```


* 3. 删除registry地址

```
npm config rm registry
```

* 4. nrm是专门用来管理和快速切换私人配置的registry【建议全局安装】

```
192:Pipeline-Node zhuruhong$ npm install nrm -g --save
npm WARN deprecated coffee-script@1.7.1: CoffeeScript on NPM has moved to "coffeescript" (no hyphen)
/usr/local/bin/nrm -> /usr/local/lib/node_modules/nrm/cli.js
+ nrm@1.2.1
added 489 packages from 840 contributors in 26.567s
192:Pipeline-Node zhuruhong$ 
```


* 5. 用nrm ls命令查看默认配置，带*号即为当前使用的配置

```
192:Pipeline-Node zhuruhong$ nrm ls

  npm -------- https://registry.npmjs.org/
  yarn ------- https://registry.yarnpkg.com/
  cnpm ------- http://r.cnpmjs.org/
* taobao ----- https://registry.npm.taobao.org/
  nj --------- https://registry.nodejitsu.com/
  npmMirror -- https://skimdb.npmjs.com/registry/
  edunpm ----- http://registry.enpmjs.org/

192:Pipeline-Node zhuruhong$ 
```


* 6. 查看当前使用的是哪个源

```
192:Pipeline-Node zhuruhong$ nrm current
taobao
192:Pipeline-Node zhuruhong$ 
```


* 7. 切换当镜像源

```
192:Pipeline-Node zhuruhong$ nrm use npm
                        

   Registry has been set to: https://registry.npmjs.org/

192:Pipeline-Node zhuruhong$
```


* 8. 添加npm源

```
192:Pipeline-Node zhuruhong$ nrm add taobao https://registry.npm.taobao.org/

    add registry taobao success

192:Pipeline-Node zhuruhong$ 
```


* 9. 测试下载速度

```
192:Pipeline-Node zhuruhong$ nrm test npm

* npm ---- 800ms

192:Pipeline-Node zhuruhong$ 
```


* 10. 删除npm源配置

```
192:Pipeline-Node zhuruhong$ nrm del taobao

    delete registry taobao success

192:Pipeline-Node zhuruhong$ 
```


* 11. 清除node的cache

```
sudo npm cache clean -f 
```


* 12. 安装"n"版本管理工具，管理node（没有错，就是n）

```
sudo npm install -g n 
```


* 13. 更新node版本

```
192:Pipeline-Node zhuruhong$ sudo npm install npm@latest -g 
Password:
/usr/local/bin/npm -> /usr/local/lib/node_modules/npm/bin/npm-cli.js
/usr/local/bin/npx -> /usr/local/lib/node_modules/npm/bin/npx-cli.js
+ npm@6.11.3
added 61 packages from 18 contributors, removed 18 packages and updated 69 packages in 42.071s
192:Pipeline-Node zhuruhong$ 
192:Pipeline-Node zhuruhong$ npm -v
6.11.3
192:Pipeline-Node zhuruhong$ 
```
