## 背景 ##

随着时代的发展，电子邮件的要求也越来越高，普通个人邮件就罢了，一旦涉及商业服务，邮件营销。那么邮件就不可避免的需要简单的HTML设计。而这两年，用户随着移动设备的使用，移动端显示效果更是纳入了电子邮件设计的考虑范围。响应式的布局自然而然的成为了邮件页面设计的必选技术。

邮件和网页不同，我们精心设计一组网页专题，其在web上存活的时间一般都比较长，设计和制作成本都比较高。而网页，特别是一些邮件订阅，基本上发布频率保持在每天或每周。如果只专注于页面的布局策划这个成本会无形中提高很多。

我考虑发起的项目，是可以使用户能够专注于内容编辑，而样式可以直接复制使用，不必经过复杂的导入导出过程，不必使用过多无用标签，即可达到邮件设计的目的。基本上该项目是一个模板项目，使用时只需要简单的复制粘贴，更改些自定义参数，添加内容即可。

## 一些注意点 ##

邮件的撰写现在实际上需要考虑以下几个要点：

1. 输出型：直接抛弃互动设计，不是互动不好，而是用户查看邮件时几乎没有在页面上等待输入结果的时间。
2. 移动为王：现在相当一部分用户是在手机浏览器或APP中直接浏览，如果不支持移动端或体验很差，用户一般会随手关闭。
3. 类型决定布局：
   + 邮件订阅最常见的是Newsletter，我们可以称为通讯或消息推送，主要是同一主题的文章简介及其链接。这种邮件内容很丰富，设计既要顾及样式又要顾及内容。
   + 邮件通知，这类邮件通常比较简短，说明一个重要的中心内容，这种邮件重在布局，如何突出重点。
   + 促销邮件，像QQ团购、Amazon推荐这类邮件，其中的内容主要依靠促销信息及描述图片进行支撑。结构尽量简单化、可以突出某几项重点信息。
4. 内容第一：邮件如果不能让用户在最短时间内明白其中的重要信息及意图，基本上就是失败的。
5. 简洁为上：无论把邮件设计的多么赏心悦目，其表达不直接不明确，达到的效果依然有限。

## 搜集到的项目 ##

### Cerberus[http://tedgoas.github.io/Cerberus/]

作者在项目中给出了两个简单DEMO，你可以使用其中布局的一部分或全部使用。并给出了两种模式，一种使用了media queries，一种没有使用。

### Ink[http://zurb.com/ink/]

Ink是由Zurb提供的一套响应式邮件设计模板。这些模板做出的邮件能在任何设备和邮件客户端使用，包括Outlook。而且非常简便。

* Ink主页[http://zurb.com/ink/]
* Ink模板[http://zurb.com/ink/templates.php]
* Ink文档[http://zurb.com/ink/docs.php]
* Ink Github[https://github.com/zurb/ink]

### Responsive Email Patterns[http://responsiveemailpatterns.com/]

Responsive Email Patterns集合了一些在创建响应式电子邮件时非常有用的模型和素材。 其中包括布局模型，导航按钮，表单，多媒体内容等等。

Responsive Email Patterns on Github[https://github.com/briangraves/ResponsiveEmailPatterns]

### Email-Framework[http://emailframe.work]

这个项目是迄今最新的响应式Email布局。

* Email-Framework主页[http://emailframe.work]
* Email-Framework Github[https://github.com/g13nn/Email-Framework]

###Antwort[http://internations.github.io/antwort/]

响应式邮件布局，现在依然持续更新中。

* Antwort主页[http://internations.github.io/antwort/]
* Antwort on Github[https://github.com/InterNations/antwort]

### 100+模板直接下载

[http://www.campaignmonitor.com/]该网站提供模板在线设计工具，收费。其中有一套成品模板下载，包含在以下地址：

https://www.campaignmonitor.com/email-templates/all/  想使用此模板的用户请尽快下载。

### Litmus[https://litmus.com/]

* Email设计测试平台，收费，提供一周免费试用。
* Email设计交流社区[https://litmus.com/community]
* Email设计学习平台[https://litmus.com/community/learning]

### MailChimp模板设计[http://templates.mailchimp.com/]

MailChimp提供的一些Email设计需要的各种知识和资源。

### Emailology[http://www.emailology.org]

提供了必要的Email排版技术和工具。可以作为参考。

## 结论 ##

我搜索了Github，基本上国内只有很少的人关注邮件页面设计。也许很多人都能够直接使用国外开源代码建立应急的方案，但是在专注这方面的使用者手里，却成为了很大的难题。基本上没有可以参考的教材，也没有相关的知识。只能靠邮件系统简单的提示进行排版和设计。

所以国人经常遇到这种情况：收到一封陌生邮件，打开一看，唔哩哇啦一大堆文字，虽然能够看懂。但看到低劣的样式，就会觉得，这种东西不可信。其中就造成了很多用户的流失。商家看不到效果，也就放弃了这种方法，使用这种邮件传播的多为大公司，能够使用有偿的邮件设计服务。

我准备建立一个仓库，为这个技术提供一个国人版的代码库和文档。使更多的人参与到使用中，也能使大家不再遭受难看邮件的侵扰。

* Author：老零[http://github.com/laoling]
* Time:2015.07.11