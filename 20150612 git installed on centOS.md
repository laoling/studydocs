#在centOS上安装git

git现已成为知名的版本控制工具，对日常编程工作有很大的帮助作用。这里我们介绍下如何在centOS6.5上安装git。

###首先我们安装在编译安装过程中需要的依赖

	># yum install curl-devel expat-devel gettext-devel  openssl-devel zlib-devel

在安装git时，首先考虑其必须的依赖包，官网列出了必要的curl、expat、gettext、zlib、openssl这些依赖，我们这里通过yum的方式对它们首先进行安装。

其次，git安装过程中make对Perl编译也需要进行支持。这里我们通过yum的方式也可以进行安装。

	># yum install perl-ExtUtils-MakeMaker

此依赖如未安装，则会在make编译过程中出现下列报错信息：

	usr/bin/perl Makefile.PL PREFIX='/usr/local/git' INSTALL_BASE='' --localedir='/usr/local/git/share/locale'
	Can't locate ExtUtils/MakeMaker.pm in @INC (@INC contains: /usr/local/lib64/perl5
	 /usr/local/share/perl5 /usr/lib64/perl5/vendor_perl
	 /usr/share/perl5/vendor_perl /usr/lib64/perl5
	 /usr/share/perl5 .) at Makefile.PL line 3.
	BEGIN failed--compilation aborted at Makefile.PL line 3.
	make[1]: *** [perl.mak] Error 2
	make: *** [perl/perl.mak] Error 2

在安装前，还要检查是否安装asciidoc，此工具在编译文档过程中是必不可少的。

	># yum install asciidoc

编译文档过程中缺少asciidoc，会报错下列信息：

	/bin/sh: line 1: asciidoc: command not found

在安装文档时，还要检查是否安装xmlto，此工具在解析完文档编译XML时必不可少。

	># yum install xmlto

如果缺少xmlto，会报错下列信息：

	/bin/sh: line 1: xmlto: command not found

也许编译过程中还会报错下列信息，是由于缺少组件libiconv：

	/utf8.c:463: undefined reference to `libiconv'

libiconv在yum源中并没有提供安装包，这里我们进行源码安装：

	># wget http://ftp.gnu.org/pub/gnu/libiconv/libiconv-1.14.tar.gz
	># tar zxvf libiconv-1.14.tar.gz 
	># cd libiconv-1.14
	># ./configure --prefix=/usr/local/libiconv
	># make && make install

到这里，git安装前需要的依赖包就全部安装完成了。

###下面我们克隆git源码

	># git clone git://git.kernel.org/pub/scm/git/git.git

或

	># git clone https://github.com/git/git


###下面我们进行git所在文件夹安装

执行以下操作:

	># cd git
	># make prefix=/usr/local all doc
	># make prefix=/usr/local install install-doc install-html

###查看我们安装的git版本

	># git version

>git version 2.4.3.368.g7974889

到这里我们就将git安装成功了，接下来就可以进行git的其他操作了。

author：老零[https://github.com/laoling]
