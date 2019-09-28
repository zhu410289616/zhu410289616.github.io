---
title: pod命令记录
date: 2019-09-16 22:45:24
tags:
- pod
---

## pod命令记录
* 指定目录，安装指定版本cocoapods

	```
	sudo gem install -n /usr/local/bin cocoapods -v 1.3.1
	```
	```
	sudo gem install cocoapods -v 0.25.0
	```

* cocoapods版本回退
	
	```
	sudo gem uninstall cocoapods
	```
	```
	sudo gem uninstall cocoapods -v 1.6.2
	```
	```
	sudo gem uninstall -n /usr/local/bin cocoapods -v 1.6.2
	```
	
* 指定版本执行pod install

	```
	pod _1.3.1_ install
	```
	
* 删除 pod search 索引

	```
	rm ~/Library/Caches/CocoaPods/search_index.json
	```


* 其他命令

	```
	pod _0.37.2_ setup
	```