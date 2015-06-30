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

这里安装asciidoc时，相关依赖会安装TeXLive完整版本，要大几百M的安装。很慢。

### 通过git命令克隆最新git库

	git clone https://github.com/git/git

### git文件夹中编译安装

	cd git
	make prefix=/usr all doc
	make prefix=/usr install install-doc install-html

查看最新版本

>git version 2.5.0.rc0.3.g912bd49

到这里我们就将git安装成功了，接下来就可以进行git的其他操作了。

## Ubuntu同样安装nodejs、npm ##

进入root下我们下载官网源码包（最新稳定版本）

	wget https://nodejs.org/dist/v0.12.5/node-v0.12.5-linux-x86.tar.gz

下载完成解压

	tar -zxvf node-v0.12.5-linux-x86.tar.gz

接下来进入源码目录编译安装

	cd node-v0.12.5
	make
	make install

`apt-get install g++ curl libssl-dev apache2-utils`，解决依赖，基本上编译没有问题，安装完成后如果找不到node 或 npm命令，我们添加一下软链接

	ln -s usr/local/bin/node /usr/bin/node
	ln -s usr/local/bin/npm /usr/bin/npm

npm添加n模块可以管理node版本

	npm install n -g

安装后，以后升级nodejs可以直接使用` n stable `升级到最新稳定版本。

npm我们这里安装下前端项目自动化套件yeoman，包含yo（脚手架工具）、grunt（构建工具）、bower（包管理器）。

	npm install yo -g
	npm install grunt-cli -g
	npm install bower -g

完成后，我的系统支持的npm包构成的树如下

	/usr/local/lib
	├── n@1.3.0
	└─┬ npm@2.11.2
	  ├── abbrev@1.0.7
	  ├── ansi@0.3.0
	  ├── ansi-regex@1.1.1
	  ├── ansicolors@0.3.2
	  ├── ansistyles@0.1.3
	  ├── archy@1.0.0
	  ├── async-some@1.0.2
	  ├── block-stream@0.0.8
	  ├── char-spinner@1.0.1
	  ├── chmodr@0.1.1
	  ├── chownr@0.0.2
	  ├── cmd-shim@2.0.1
	  ├─┬ columnify@1.5.1
	  │ └─┬ wcwidth@1.0.0
	  │   └─┬ defaults@1.0.2
	  │     └── clone@0.1.19
	  ├─┬ config-chain@1.1.9
	  │ └── proto-list@1.2.4
	  ├─┬ dezalgo@1.0.2
	  │ └── asap@1.0.0
	  ├── editor@1.0.0
	  ├── fs-vacuum@1.2.6
	  ├── fs-write-stream-atomic@1.0.3
	  ├── fstream@1.0.6
	  ├─┬ fstream-npm@1.0.2
	  │ └── fstream-ignore@1.0.2
	  ├── github-url-from-git@1.4.0
	  ├── github-url-from-username-repo@1.0.2
	  ├─┬ glob@5.0.10
	  │ └── path-is-absolute@1.0.0
	  ├── graceful-fs@3.0.8
	  ├── hosted-git-info@2.1.4
	  ├── inflight@1.0.4
	  ├── inherits@2.0.1
	  ├── ini@1.3.3
	  ├─┬ init-package-json@1.6.0
	  │ ├── promzard@0.3.0
	  │ └─┬ validate-npm-package-license@1.0.0-prerelease-2
	  │   └── spdx-correct@1.0.0-prerelease-3
	  ├── lockfile@1.0.1
	  ├── lru-cache@2.6.4
	  ├─┬ minimatch@2.0.8
	  │ └─┬ brace-expansion@1.1.0
	  │   ├── balanced-match@0.2.0
	  │   └── concat-map@0.0.1
	  ├─┬ mkdirp@0.5.1
	  │ └── minimist@0.0.8
	  ├─┬ node-gyp@2.0.1
	  │ ├─┬ glob@4.5.3
	  │ │ └─┬ minimatch@2.0.8
	  │ │   └─┬ brace-expansion@1.1.0
	  │ │     ├── balanced-match@0.2.0
	  │ │     └── concat-map@0.0.1
	  │ ├─┬ minimatch@1.0.0
	  │ │ └── sigmund@1.0.1
	  │ ├─┬ path-array@1.0.0
	  │ │ └─┬ array-index@0.1.1
	  │ │   └─┬ debug@2.2.0
	  │ │     └── ms@0.7.1
	  │ └── tar@1.0.3
	  ├── nopt@3.0.2
	  ├── normalize-git-url@1.0.1
	  ├── normalize-package-data@2.2.0
	  ├── npm-cache-filename@1.0.1
	  ├── npm-install-checks@1.0.5
	  ├── npm-package-arg@4.0.1
	  ├─┬ npm-registry-client@6.4.0
	  │ └─┬ concat-stream@1.4.8
	  │   └── typedarray@0.0.6
	  ├── npm-user-validate@0.1.2
	  ├─┬ npmlog@1.2.1
	  │ ├─┬ are-we-there-yet@1.0.4
	  │ │ └── delegates@0.1.0
	  │ └─┬ gauge@1.2.0
	  │   ├── has-unicode@1.0.0
	  │   ├── lodash._basetostring@3.0.0
	  │   ├─┬ lodash._createpadding@3.6.0
	  │   │ └── lodash.repeat@3.0.0
	  │   ├── lodash.pad@3.1.0
	  │   ├── lodash.padleft@3.1.1
	  │   └── lodash.padright@3.1.1
	  ├── once@1.3.2
	  ├── opener@1.4.1
	  ├── osenv@0.1.1
	  ├── path-is-inside@1.0.1
	  ├─┬ read@1.0.6
	  │ └── mute-stream@0.0.5
	  ├─┬ read-installed@4.0.0
	  │ ├── debuglog@1.0.1
	  │ ├── readdir-scoped-modules@1.0.1
	  │ └── util-extend@1.0.1
	  ├─┬ read-package-json@2.0.0
	  │ └─┬ json-parse-helpfulerror@1.0.3
	  │   └── jju@1.2.0
	  ├─┬ readable-stream@1.1.13
	  │ ├── core-util-is@1.0.1
	  │ ├── isarray@0.0.1
	  │ └── string_decoder@0.10.31
	  ├── realize-package-specifier@3.0.1
	  ├─┬ request@2.57.0
	  │ ├── aws-sign2@0.5.0
	  │ ├─┬ bl@0.9.4
	  │ │ └─┬ readable-stream@1.0.33
	  │ │   ├── core-util-is@1.0.1
	  │ │   ├── isarray@0.0.1
	  │ │   └── string_decoder@0.10.31
	  │ ├── caseless@0.10.0
	  │ ├─┬ combined-stream@1.0.3
	  │ │ └── delayed-stream@1.0.0
	  │ ├── forever-agent@0.6.1
	  │ ├─┬ form-data@0.2.0
	  │ │ ├── async@0.9.2
	  │ │ └─┬ combined-stream@0.0.7
	  │ │   └── delayed-stream@0.0.5
	  │ ├─┬ har-validator@1.7.1
	  │ │ ├── bluebird@2.9.27
	  │ │ ├─┬ chalk@1.0.0
	  │ │ │ ├── ansi-styles@2.0.1
	  │ │ │ ├── escape-string-regexp@1.0.3
	  │ │ │ ├─┬ has-ansi@1.0.3
	  │ │ │ │ └── get-stdin@4.0.1
	  │ │ │ └── supports-color@1.3.1
	  │ │ ├─┬ commander@2.8.1
	  │ │ │ └── graceful-readlink@1.0.1
	  │ │ └─┬ is-my-json-valid@2.12.0
	  │ │   ├── generate-function@2.0.0
	  │ │   ├─┬ generate-object-property@1.2.0
	  │ │   │ └── is-property@1.0.2
	  │ │   ├── jsonpointer@1.1.0
	  │ │   └── xtend@4.0.0
	  │ ├─┬ hawk@2.3.1
	  │ │ ├── boom@2.7.2
	  │ │ ├── cryptiles@2.0.4
	  │ │ ├── hoek@2.14.0
	  │ │ └── sntp@1.0.9
	  │ ├─┬ http-signature@0.11.0
	  │ │ ├── asn1@0.1.11
	  │ │ ├── assert-plus@0.1.5
	  │ │ └── ctype@0.5.3
	  │ ├── isstream@0.1.2
	  │ ├── json-stringify-safe@5.0.1
	  │ ├─┬ mime-types@2.0.12
	  │ │ └── mime-db@1.10.0
	  │ ├── node-uuid@1.4.3
	  │ ├── oauth-sign@0.8.0
	  │ ├── qs@3.1.0
	  │ ├── stringstream@0.0.4
	  │ ├── tough-cookie@1.2.0
	  │ └── tunnel-agent@0.4.0
	  ├── retry@0.6.1
	  ├─┬ rimraf@2.3.4
	  │ └── glob@4.5.3
	  ├── semver@4.3.6
	  ├── sha@1.3.0
	  ├── slide@1.1.6
	  ├── sorted-object@1.0.0
	  ├─┬ spdx@0.4.0
	  │ └── spdx-license-ids@1.0.0
	  ├── strip-ansi@2.0.1
	  ├── tar@2.1.1
	  ├── text-table@0.2.0
	  ├── uid-number@0.0.6
	  ├── umask@1.1.0
	  ├─┬ validate-npm-package-name@2.2.0
	  │ └── builtins@0.0.7
	  ├─┬ which@1.1.1
	  │ └─┬ is-absolute@0.1.7
	  │   └── is-relative@0.1.3
	  ├── wrappy@1.0.1
	  └── write-file-atomic@1.1.2

author：老零[https://github.com/laoling]
