---
title: 安装brew和node
date: 2019-09-06 11:17:59
tags: 
- hexo
- node
---

## 安装brew和node
* 1.安装brew：官方指导地址 [https://brew.sh/index_zh-cn](https://brew.sh/index_zh-cn)

* 2.检查brew是否已经安装：brew -v

```
192:RHSocketKit zhuruhong$ brew -v
Homebrew 2.1.11
Homebrew/homebrew-core (git revision dabec; last commit 2018-11-10)
192:RHSocketKit zhuruhong$ 
```

* 3.安装node：brew install node

```
192:RHSocketKit zhuruhong$ brew install node
Updating Homebrew...
^C==> Installing dependencies for node: icu4c
==> Installing node dependency: icu4c
==> Downloading https://homebrew.bintray.com/bottles/icu4c-62.1.high_sierra.bottle.tar.gz
==> Downloading from https://akamai.bintray.com/d1/d1c24fa3df7e89935554ebcdbc6de6363cab0d264f01902db17eda35d8df0333?__gda__=exp=1567695743~hmac=06f23110c0c5
######################################################################## 100.0%
==> Pouring icu4c-62.1.high_sierra.bottle.tar.gz
==> Caveats
icu4c is keg-only, which means it was not symlinked into /usr/local,
because macOS provides libicucore.dylib (but nothing else).

If you need to have icu4c first in your PATH run:
  echo 'export PATH="/usr/local/opt/icu4c/bin:$PATH"' >> ~/.bash_profile
  echo 'export PATH="/usr/local/opt/icu4c/sbin:$PATH"' >> ~/.bash_profile

For compilers to find icu4c you may need to set:
  export LDFLAGS="-L/usr/local/opt/icu4c/lib"
  export CPPFLAGS="-I/usr/local/opt/icu4c/include"

For pkg-config to find icu4c you may need to set:
  export PKG_CONFIG_PATH="/usr/local/opt/icu4c/lib/pkgconfig"

==> Summary
🍺  /usr/local/Cellar/icu4c/62.1: 250 files, 67.3MB
==> Installing node
==> Downloading https://homebrew.bintray.com/bottles/node-11.1.0.high_sierra.bottle.tar.gz
==> Downloading from https://akamai.bintray.com/fe/fe56eea71f6ce71212b5ca75003da31833d713fa64743cf07335c0390b82765f?__gda__=exp=1567695887~hmac=e96d72e778d8
######################################################################## 100.0%
==> Pouring node-11.1.0.high_sierra.bottle.tar.gz
==> Caveats
Bash completion has been installed to:
  /usr/local/etc/bash_completion.d
==> Summary
🍺  /usr/local/Cellar/node/11.1.0: 3,936 files, 47.0MB
==> `brew cleanup` has not been run in 30 days, running now...
Removing: /Users/zhuruhong/Library/Caches/Homebrew/libevent--2.1.8.high_sierra.bottle.tar.gz... (753KB)
Removing: /usr/local/Cellar/libtool/2.4.6... (70 files, 3.7MB)
Removing: /usr/local/Cellar/openssl/1.0.2f... (1,651 files, 11.9MB)
Removing: /usr/local/Cellar/openssl/1.0.2n... (1,792 files, 12.3MB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/openssl--1.0.2p.high_sierra.bottle.tar.gz... (3.7MB)
Removing: /usr/local/Cellar/pkg-config/0.29... (10 files, 621.5KB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/automake-1.15.1.high_sierra.bottle.tar.gz... (915.4KB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/bazel-0.9.0.high_sierra.bottle.tar.gz... (91.4MB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/gdbm-1.13.high_sierra.bottle.tar.gz... (182.3KB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/gettext-0.19.8.1.high_sierra.bottle.tar.gz... (7.8MB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/libidn2-2.0.4.high_sierra.bottle.tar.gz... (190.4KB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/libtool-2.4.6_1.high_sierra.bottle.tar.gz... (1009.5KB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/libunistring-0.9.8.high_sierra.bottle.tar.gz... (1.4MB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/openssl-1.0.2n.high_sierra.bottle.tar.gz... (3.7MB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/openssl@1.1-1.1.0g.high_sierra.bottle.tar.gz... (4.5MB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/pkg-config-0.29.2.high_sierra.bottle.tar.gz... (235.8KB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/portable-ruby-2.3.7.leopard_64.bottle.tar.gz... (7.4MB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/python3--pip-9.0.1.tar.gz... (1.1MB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/python3--setuptools-36.5.0.zip... (704.6KB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/python3--wheel-0.30.0.tar.gz... (42KB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/python3-3.6.4.tar.xz... (16.2MB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/readline-7.0.3_1.high_sierra.bottle.tar.gz... (495.5KB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/sqlite-3.21.0.high_sierra.bottle.tar.gz... (1.4MB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/wget-1.19.2_1.high_sierra.bottle.tar.gz... (1.3MB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/xz-5.2.3.high_sierra.bottle.tar.gz... (459.5KB)
Removing: /Users/zhuruhong/Library/Caches/Homebrew/Cask/java--9.0.1,11.dmg... (382.1MB)
Removing: /Users/zhuruhong/Library/Logs/Homebrew/automake... (68B)
Removing: /Users/zhuruhong/Library/Logs/Homebrew/bazel... (68B)
Removing: /Users/zhuruhong/Library/Logs/Homebrew/carthage... (3.7KB)
Removing: /Users/zhuruhong/Library/Logs/Homebrew/eye-d3... (10.5KB)
Removing: /Users/zhuruhong/Library/Logs/Homebrew/gdbm... (68B)
Removing: /Users/zhuruhong/Library/Logs/Homebrew/gettext... (68B)
Removing: /Users/zhuruhong/Library/Logs/Homebrew/jenkins... (56.1KB)
Removing: /Users/zhuruhong/Library/Logs/Homebrew/libevent... (68B)
Removing: /Users/zhuruhong/Library/Logs/Homebrew/libidn2... (68B)
Removing: /Users/zhuruhong/Library/Logs/Homebrew/libtool... (68B)
Removing: /Users/zhuruhong/Library/Logs/Homebrew/libunistring... (68B)
Removing: /Users/zhuruhong/Library/Logs/Homebrew/openssl... (68B)
Removing: /Users/zhuruhong/Library/Logs/Homebrew/openssl@1.1... (68B)
Removing: /Users/zhuruhong/Library/Logs/Homebrew/pkg-config... (7 files, 1018.0KB)
Removing: /Users/zhuruhong/Library/Logs/Homebrew/python3... (12 files, 4.6MB)
Removing: /Users/zhuruhong/Library/Logs/Homebrew/readline... (68B)
Removing: /Users/zhuruhong/Library/Logs/Homebrew/sqlite... (68B)
Removing: /Users/zhuruhong/Library/Logs/Homebrew/wget... (68B)
Removing: /Users/zhuruhong/Library/Logs/Homebrew/xz... (5 files, 1.1MB)
Pruned 24 symbolic links and 4 directories from /usr/local
==> Caveats
==> icu4c
icu4c is keg-only, which means it was not symlinked into /usr/local,
because macOS provides libicucore.dylib (but nothing else).

If you need to have icu4c first in your PATH run:
  echo 'export PATH="/usr/local/opt/icu4c/bin:$PATH"' >> ~/.bash_profile
  echo 'export PATH="/usr/local/opt/icu4c/sbin:$PATH"' >> ~/.bash_profile

For compilers to find icu4c you may need to set:
  export LDFLAGS="-L/usr/local/opt/icu4c/lib"
  export CPPFLAGS="-I/usr/local/opt/icu4c/include"

==> node
Bash completion has been installed to:
  /usr/local/etc/bash_completion.d
192:RHSocketKit zhuruhong$ 
```

* 4.确认node版本： npm -v

```
192:RHSocketKit zhuruhong$ npm -v
6.4.1
192:RHSocketKit zhuruhong$ 
```

* 5.使用npm：官网地址 [https://www.npmjs.com/](https://www.npmjs.com/)
