---
date: 2020-4-3
tag: 
  - git
author: Ramsey
location: Suzhou  
---
# git push出现ssh_dispatch_run_fatal错误

>ssh_dispatch_run_fatal: Connection to 52.74.223.119 port 22: Software caused connection abort
fatal: Could not read from remote repository.
Please make sure you have the correct access rights
and the repository exists.

#### 报错原因

dns解析问题，打开cmd输入`ping`命令查看对github.com的连接，发现请求超时
![在这里插入图片描述](https://img-blog.csdnimg.cn/20200404222346121.png)

#### 解决方法

在 `C:\Windows\System32\drivers\etc`下的 **hosts** 文件中，在末尾添加下面两段文字即可
```
192.30.255.112  github.com git 
185.31.16.184 github.global.ssl.fastly.net
```
保存之后再次输入`ping`命令，成功ping通
![在这里插入图片描述](https://img-blog.csdnimg.cn/2020040422312342.png)

再次git push没有问题，亲测有效，特意做个笔记。

**参考链接：**[https://segmentfault.com/a/1190000021795122](https://segmentfault.com/a/1190000021795122)
