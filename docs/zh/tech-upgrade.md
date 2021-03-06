# 更新

Web技术日新月异，更新升级是维护工作之一，长时间不更新（升级）的程序，就如长时间不维护的建筑物一样，会加速老化、功能逐渐缺失直至无法使用。

## 对象

一台服务器包括：**操作系统、运行环境、数据库和应用程序**四个部分，其对应的升级对象也是此四部分。

## 更新 VS 升级

更新或升级这两个词有相近之处，虽然都是从低版本到高版本，但仔细体会它们也有明显的差异。

在实际升级工作中，主要存在两种形式的版本变化目标：

- **大版本变化**，例如：MySQL5.6->MySQL5.7，PHP5.6->PHP7.0  
- **小版本变化**，例如：MySQL5.6.25-->MySQL5.6.30，PHP5.6.33->PHP5.6.37

程序的大版本变化，是从功能上、架构上都有显著的改变（质变），升级过程复杂，存在升级失败的风险
程序的小版本变化，是从补丁漏洞的角度上提供的更新内容（量变），升级过程相对简单

总结：大版本变化为“**升级**”，小版本变化为“**更新**”

> 升级之前，请做好备份

## 方案

本方案主要提供更新方案，完成更新之后，操作系统和环境的漏洞基本都会更新。

### Linux更新

Linux服务器的更新，只需要运行一条更新命令，即可安装操作系统、运行环境和数据库等更新

```
#CentOS or Redhat
sudo yum update -y

#Ubuntu
apt update && apt upgrade -y
```

实际上，Websoft9提供的镜像已经将以上更新命令通过计划任务定期执行。

### Windows更新

Windows服务器的更新与本地电脑类似，手动找到更新管理程序，设置自动下载自动更新即可。

Windows服务器中的运行环境、数据库等，需要采用手工下载补丁替换的方式完成更新

