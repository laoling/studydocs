#CSS:自定义web中文字体

在现今表现丰富的网页中，一部分人们惊叹外文网站字体的丰富，一部分则抱怨浏览中文网页，文字内容的字体过来过去就几种，表现也有点过于贫乏了。事实上，这个问题现今基本上已经找到合适的解决方案，你也可以通过一定的技术在网页上自由使用丰富的中文字体了。

###CSS @font-face

@font-face规则是css中为实现调用服务器字体资源而制定的。我们先看看其定义格式：

	@font-face {
      font-family: <YourWebFontName>;
      src: <source> [<format>][,<source> [<format>]]*;
      [font-weight: <weight>];
      [font-style: <style>];
    }

我们大概在2012年出版的图书中可以看到自定义字体在浏览器的支持情况，大体来说是这个样子的：

* 微软IE支持自有的.eot(Embedded Open Type)格式
* Safari自3.1开始支持.ttf(TureType)和.otf(OpenType)格式，另外支持.svg(SVG Font)格式
* Firefox自3.6开始支持.ttf(TureType)，.otf(OpenType)格式和.woff(Web Open Font Format)格式
* Chrome支持.ttf(TureType)和.otf(OpenType)格式，另外支持.svg(SVG Font)格式
* Opera支持.ttf(TureType)和.otf(OpenType)格式，另外支持.svg(SVG Font)格式

实际上这个支持情况已经有了比较大的变动，情况如下：

1. .woff支持情况的变化：这个由W3CWeb字体工作小组进行标准化的字体格式，已成为多浏览器的推荐格式。Firefox3.6起，WebKit全面支持，Safari自5.1起，Chrome自5.0起，IE自9起。
2. 现在我们在引入web-font时，基本上是引入四个字体文件，对游览器字体支持进行全兼容处理：.ttf、.eot、.woff、.svg。

###@font-face的例子

这里我们假定有一个fontName.ttf字体，我们可以通过以下方式在网页中进行引用。

	@font-face { 
	  font-family: 'fontName';  /* 字体名称,可自己定义 */
	  src: url('fontName.eot'); 
	  src: local('fontName Regular'),
	       local('fontName'), 
	       url('fontName.woff') format('woff'), 
	       url('fontName.ttf') format('truetype'),  
	       url('fontName.svg#fontName') format('svg');
	}

当然，在网页中如果使用完整的字体文件，中文字体会出现文件过大，字体加载缓慢或加载不上的情况。一方面，我们希望网络能够使网速更进一步发展，这里就不说了，只是个期望。另一方面，这种情况我们进行以下处理。

我们将字体文件中将会使用到的文字从字体文件中抽取出来，做成比较小的字体文件，并通过一些工具生成可能会使用到的其他字体文件。

这里我记录一款国人制作的字体生成程序，字蛛（FontSpider）[https://github.com/aui/font-spider]

本文作者：老零[https://github.com/laoling]