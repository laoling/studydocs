# 使用Emmet

最近经常会遇到写页面的活儿，一个标签一个标签去打，觉得很麻烦。之前看到过Emmet的介绍，就尝试使用一下。其中对html和css的结构化编写，使用简单的语法仅能够轻松达成。这里先简单介绍一下。

## Emmet

	Emmet主页： http://www.emmet.io
	Emmet文档： http://docs.emmet.io
	Emmet on Github： https://github.com/emmetio

下面这段介绍来源于官方主页：

* CSS式写HTML
	* 你已经知道怎么去使用Emmet缩写：它的灵感来源于CSS选择器。
* 动态的代码片段
	* 每个缩写都会在运行时转换：只是稍微改变它的名字就能获得不同的结果。
* 超快编写代码
	* 使用Emmet你可以快速书写一堆代码，用新标签包裹代码，快速遍历并且选择重要代码部分或更多！
* 可定制
	* 用户可以很容易添加新片段，使用几个JSON文件调整Emmet编程体验。
* 新工具平台
	* 深入研究Emmet源代码，重用其模块创建你自有独特的行为。
* 高度可移植性
	* Emmet是使用纯Javascript编写的，并跨平台工作：浏览器、Node.js、微软WSH、Mozilla犀牛。

## Emmet安装

这里我只介绍两种常用工具安装Emmet。Nodepad++和Sublime Text3.

### 1、Sublime Text3

安装步骤：

1. 安装Package Control。
2. 打开Package Control：Install Package。
3. 输入Emmet。
4. 单击即可安装。

### 2、Nodepad++

安装步骤：

1. 一般我们安装完毕Nodepad++后，默认插件中会有Plugin Manager。选择安装Emmet，可能会无法使用。
2. 我们首先安装插件Python Script。地址：[http://sourceforge.net/projects/npppythonscript/files/Python%20Script%201.0.8.0/PythonScript_1.0.8.0.msi/download ]建议直接安装此.msi版本，只需要指定Nodepad++安装目录，他就会将组件进行注册。
3. 打开Plugin Manager，在Emmet前打钩，点击Install。
4. 重启Nodepad++，就可以正常使用了。
5. 这里更换下快捷键，设置>管理快捷键...>Plugin commands，将Expand abbreviation快捷键设为Tab。就可以使用Tab进行转换执行了。

## 快速编写HTML



