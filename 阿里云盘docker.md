# 阿里云盘Webdav实现本地挂载教程---docker容器运行

## 温馨提示

* 本篇教程操作需要一定的计算机知识和动手能力，纯小白可以直接放弃了
* docker desktop 安装有很大可能会出现问题
* docker 需要启动某些windows功能（比如Hyper-v功能），家庭版windows可能会无法找到这些功能
* 由于国外网站可能加载比较慢，请结合加速器以提高体验

## 教学平台

* 本教程适用于 Windows 10 系统

## 使用到的软件

* RailDrive [官方下载](https://dw85.uptodown.com/dwn/3pafw1bUyb46bYs-x-qhYEv1DUGW-K3652EEB8T1NZMo1AWcTLZdmsIo3YIBzs7zW_NlIAr2WPB-Fh4CPDa_n8M6b2WT7QiFpp-XfXzYlWkBc9sfGVOXNQAm3CqMV1ro/LLsYOxrCPB4x3vMqkwwxd1pt1CmrV1ZO9-HsadS_OXqqYFzIGQMnSiMjSYDA8RPEp2BL0LWvExOelJ8SJsZv5A9w0967FNIFvcGgQQ9FXtmKT4Tq9mexK_VunzbCtCtv/sIoURY9Mbev1KTTCMV6wNmUM0b-29Gju_KTUCSAHxHKUb63q47R28b3P0p4ZQkVjCMbo3uMrZIDpj9sm8JGthQ==/raidrive-2021-5-20.exe)  [云盘分享](https://www.aliyundrive.com/s/jsBxXFgPhig)
* Docker desktop [官方下载](https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe)  [云盘分享](https://www.aliyundrive.com/s/Y4Z7u87emoU)

## 涉及的网站

[docker hub](https://hub.docker.com/)

[阿里云盘 - 公测进行中·阿里巴巴集团出品 (aliyundrive.com)](https://www.aliyundrive.com/)



## 教程开始

第一步

安装配置Docker desktop（这步会遇到一些问题，请自行解决，我就当你已经安装并且启动成功了）

第二步

获取镜像 打开网站https://hub.docker.com/

搜索框上搜索 阿里云盘

选第一个（下载量最多的）点进去，得到以下命令复制下来

```bash
docker pull zx5253/webdav-aliyundriver
```

第三步

下载镜像

打开powershell（win + x），或者win + r 启动运行，在里面输入powershell

在powershell里面粘贴之前复制的代码，回车

第四步

获取你阿里云盘账号的refreshToken

在网页上登录你的阿里云盘

[阿里云盘 - 公测进行中·阿里巴巴集团出品 (aliyundrive.com)](https://www.aliyundrive.com/)

登录成功后，按 F12 打开开发者工具，点击 Application，点击 Local Storage，点击 Local Storage 下的 https://www.aliyundrive.com/，点击右边 的 token，此时可以看到里面的数据，其中就有 refresh_token，把其值复 制出来即可。

第五步

运行该镜像

在运行镜像之前，得先把你的refresh token替换成你的

```bash
docker run -d --name=webdav-aliyundriver --restart=always -p 8080:8080  -v /etc/localtime:/etc/localtime -v /etc/aliyun-driver/:/etc/aliyun-driver/ -e TZ="Asia/Shanghai" -e ALIYUNDRIVE_REFRESH_TOKEN="your refreshToken" -e ALIYUNDRIVE_AUTH_PASSWORD="admin" -e JAVA_OPTS="-Xmx1g" zx5253/webdav-aliyundriver

# 参数说明
# /etc/aliyun-driver/ 挂载卷自动维护了最新的refreshToken，建议挂载
# ALIYUNDRIVE_AUTH_PASSWORD 是admin账户的密码，建议修改
# JAVA_OPTS 可修改最大内存占用，比如 -e JAVA_OPTS="-Xmx512m" 表示最大内存限制为512m
```

在powershell中输入上述已经修改好的命令，打开docker desktop

就可以看到正在运行的镜像了

第六步--使用raildrive挂载到本地磁盘

* 地址：这个不要勾选
* http：这个是Docker运行的电脑IP，本机填127.0.0.1 
* 端口：默认8080，这是docker命令指定的端口 ，应该填你自已设定的端口
* 账号密码：默认admin



