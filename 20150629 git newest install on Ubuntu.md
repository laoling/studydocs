# 在Ubuntu系统中安装最新的git版本 #

我们的思路和前面在centOS中安装是一样的，先默认安装为系统软件包提供版本，再通过git命令，克隆最新的git代码仓库，从源码再进行一次编译，使其更新为最新的版本。

### 安装默认版本

首先我们通过apt-get命令安装软件包提供的版本（root下）

	apt-get install git

查看安装的版本号

	git --version

我的Ubuntu15.04显示情况如下

>git version 2.1.4

是一个比较新的版本，我们下面将其升级为最新版本。

### 安装依赖

通过apt-get安装官网需要的基本依赖

	apt-get install libcurl4-gnutls-dev libexpat1-dev gettext libz-dev libssl-dev

下面安装编译文档需要的依赖

	apt-get install asciidoc xmlto

### 通过git命令克隆最新git库

	git clone https://github.com/git/git

### git文件夹中编译安装

	cd git
	make prefix=/usr/local all doc
	make prefix=/usr/local install install-doc install-html




