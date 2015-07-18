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

### 1、初始化页面

HTML文档包含一些固定的格式，比如<html><head><body>等等，你可以很容易通过几个字符的输入格式化html页面：

+ `html:5`或`!`  用于HTML5文档类型
+ `html:xt`  用于XHTML过渡文档类型
+ `html:4s`  用于HTML4严格文档类型

结果如下：

```html
> html:5
> !

<!doctype html>
<html lang="en">
<head>
	<meta charset="UTF-8">
	<title>Document</title>
</head>
<body>
	
</body>
</html>

> html:xt

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
	<meta http-equiv="Content-Type" content="text/html;charset=UTF-8">
	<title>Document</title>
</head>
<body>
	
</body>
</html>

> html:4s

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<html lang="en">
<head>
	<meta http-equiv="Content-Type" content="text/html;charset=UTF-8">
	<title>Document</title>
</head>
<body>
	
</body>
</html>
```

### 2、轻松添加类、id、文本和属性 

连续输入元素名称和ID，Emmet会自动为你补全。例如：

```html
> p#foo

<p id="foo"></p>
```

连续输入元素名称和类，Emmet会自动为你补全。例如：

```html
> p.bar

<p class="bar"></p>
```

连续输入类和id，比如p.bar#foo，会自动生成：

```html
> p.bar#foo

<p class="bar" id="foo"></p>
```

不加元素名称，直接输入ID或类，会自动生成div,有父元素的会根据父元素生成：

```html
> .bar

<div class="bar"></div>

> #foo

<div id="foo"></div>

> .bar#foo

<div class="bar" id="foo"></div>

> <ul>
> .item#foo
> </ul>

<ul>
	<li class="item" id="foo"></li>
</ul>
```

下面来看看如何定义HTML元素的内容和属性。你可以通过输入h1{foo}和a[href=#]，就可以自动生成如下代码：

```html
> h1{foo}

<h1>foo</h1>

> a[href=#]

<a href="#"></a>
```

### 3、代码嵌套

我们一般通过下面三个符号进行标签嵌套：

+ \>：  子元素符号
+ +：  同级标签符号
+ ^：  使符号后的标签提升一级

生成后代>：

大于号表示后面要生成的内容是当前标签的后代。例如：

```html
> div>ul>li>a>img

<div>
	<ul>
		<li><a href=""><img src="" alt=""></a></li>
	</ul>
</div>
```

生成兄弟+：

想要生成平级的元素，就需要使用 + 号。例如：

```html
> div+p+bq

<div></div>
<p></p>
<blockquote></blockquote>
```

生成上级元素^：

上级 （Climb-up）元素是什么意思呢？前面咱们说过了生成下级元素的符号“>”，当使用 div>ul>li 的指令之后，再继续写下去，那么后续内容都是在 li 下级的。如果我想编写一个跟 ul 平级的 span 标签，那么我需要先用 “^” 提升一下层次。例如：

```html
> div>ul>li^span

<div>
	<ul>
		<li></li>
	</ul>
	<span></span>
</div>

> 将span生成相对于div平级的元素
> div>ul>li^^span

<div>
	<ul>
		<li></li>
	</ul>
</div>
<span></span>
```

### 4、重复多个元素

要重复多个元素，可以使用*符号。例如：

```html
> ul>li*5

<ul>
	<li></li>
	<li></li>
	<li></li>
	<li></li>
	<li></li>
</ul>
```

### 5、代码分组

可以通过嵌套和括号来快速生成一些代码块，比如：

```html
> (.foo>h1)+(.bar>h2)

<div class="foo">
	<h1></h1>
</div>
<div class="bar">
	<h2></h2>
</div>

> div>(header>ul>li*2>a)+footer>p

<div>
	<header>
		<ul>
			<li><a href=""></a></li>
			<li><a href=""></a></li>
		</ul>
	</header>
	<footer>
		<p></p>
	</footer>
</div>
```

### 6、内容编号

生成多个元素时，想给元素的类或ID进行编号，就需要使用$，就可以依次递增排列序号。例如：

```html
> ul>li.item$*5

<ul>
	<li class="item1"></li>
	<li class="item2"></li>
	<li class="item3"></li>
	<li class="item4"></li>
	<li class="item5"></li>
</ul>
```
$ 就表示一位数字，只出现一个的话，就从1开始。如果出现多个，就从0开始。如果我想生成三位数的序号，那么要写三个 $：

```html
> ul>li.item$$$*5

<ul>
	<li class="item001"></li>
	<li class="item002"></li>
	<li class="item003"></li>
	<li class="item004"></li>
	<li class="item005"></li>
</ul>
```

我们也可以在 $ 后面增加 @- 来实现倒序排列：

```html
> ul>li.item$@-*5

<ul>
	<li class="item5"></li>
	<li class="item4"></li>
	<li class="item3"></li>
	<li class="item2"></li>
	<li class="item1"></li>
</ul>
```

我们也可以使用 @N 指定开始的序号：

```html
> ul>li.item$@4*5

<ul>
	<li class="item4"></li>
	<li class="item5"></li>
	<li class="item6"></li>
	<li class="item7"></li>
	<li class="item8"></li>
</ul>
```

也可以倒序与制定序号结合，如：

```html
> ul>li.item$@-2*6

<ul>
	<li class="item7"></li>
	<li class="item6"></li>
	<li class="item5"></li>
	<li class="item4"></li>
	<li class="item3"></li>
	<li class="item2"></li>
</ul>
```

## 其他快速代码

Emmet不仅仅能够生成html代码，还能够进行css和xsl的快速编写。这里就不详细介绍了。后面会添加一个相应的Emmet API页面。

* Author：老零[http://github.com/laoling]