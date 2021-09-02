#‌阿里云盘映射到本地磁盘教程

##准备工具

-------------------------------------------------

首先需要准备的工具有:
java
raidrive
#‌#安装软件

---------------------------------------------------------------------------

安装java(以下提供文件一键打包)

*java官方下载链接（9.2）

<https://sdlc-esd.oracle.com/ESD6/JSCDL/jdk/8u301-b09/d3c52aa6bfa54d3ca74e617f18309292/JavaSetup8u301.exe?GroupName=JSC&FilePath=/ESD6/JSCDL/jdk/8u301-b09/d3c52aa6bfa54d3ca74e617f18309292/JavaSetup8u301.exe&BHost=javadl.sun.com&File=JavaSetup8u301.exe&AuthParam=1630544859_996bd1cbf99cb607c3656c67ee696e10&ext=.exe>

*raidrive的官方下载地址(一般情况下下载速度会很慢):
<https://dw85.uptodown.com/dwn/3pafw1bUyb46bYs-x-qhYEv1DUGW-K3652EEB8T1NZMo1AWcTLZdmsIo3YIBzs7zW_NlIAr2WPB-Fh4CPDa_n8M6b2WT7QiFpp-XfXzYlWkBc9sfGVOXNQAm3CqMV1ro/LLsYOxrCPB4x3vMqkwwxd1pt1CmrV1ZO9-HsadS_OXqqYFzIGQMnSiMjSYDA8RPEp2BL0LWvExOelJ8SJsZv5A9w0967FNIFvcGgQQ9FXtmKT4Tq9mexK_VunzbCtCtv/sIoURY9Mbev1KTTCMV6wNmUM0b-29Gju_KTUCSAHxHKUb63q47R28b3P0p4ZQkVjCMbo3uMrZIDpj9sm8JGthQ==/raidrive-2021-5-20.exe>

*raidrive阿里云盘下载地址:
 链接：<https://www.aliyundrive.com/s/qqWi3mnT44n>

*raidrive ipfs网盘下载地址(打开浏览器粘贴链接直接下载，优先使用):

<https://ipfs.fleek.co/ipfs/QmPh1HYH3oUcqus7PhNv1vqPpZ7nGnN6cJeFrSgJ3mzyLo>

下载完成后手动改名，文件后缀加上 .exe

*阿里云盘实现Webdav（单独的软件，有能力的自己折腾）：

项目地址[^*]：<https://github.com/zxbu/webdav-aliyundriver>

[^*]:喝水不忘挖井人

文件一键打包下载地址：

<https://ipfs.fleek.co/ipfs/QmeaNaRUZ77GKCQPGn6Hb4xDVeeyWtF3KxEC8BMN4vPmMX>

百度云：

https://pan.baidu.com/s/1uQp5eSSHEzfWLWAOr-T2vA

提取码：8888

下载完成后，确认java  raidrive 已安装完成
#‌#获取token

---

打开浏览器输入阿里云盘网页版网址：
[阿里云盘 - 公测进行中·阿里巴巴集团出品 (aliyundrive.com)](https://www.aliyundrive.com/)
点击右上角进行网页版登录操作
登录成功后，打开开发者工具(按F12，或者在网页页面右键点击检查)，



上面的功能栏切换到Application,左侧栏切换到Local Storage,展开选择那唯一一项



然后在中间框选中token,在最下方的框中下滑找到refresh_token,复制引号里面的值

##运行实现软件

-----------------------------

将文件一键打包的压缩包解压

里面有两个.bat后缀名的文件，右键其中一个，选择“编辑”



将引号里面的内容和引号本身（也就是上图选中内容）替换为自己之前在浏览器获得的refresh_token

点击左上角“文件”，选择保存

然后另外一个.bat的文件也执行上述操作

##运行程序

--------------------------

如果之前没有安装好java，则双击运行“启动.bat”这一个文件

如果已安装好java,随便运行其中一个



出现上诉截图已经表明已运行服务(使用时不能关闭这个黑框框)

##连接到Webdav

-------

打开raidrive

右上角点击“添加”，服务类型选择NAS中的Webdav

按照如图所示的这样设置

特别注意要取消勾选地址旁边的小勾

账号密码都是admin

完成后点击确定





点击三角形符号，开始连接

成功之后就会在资源管理器中看到一个网络位置了



 
