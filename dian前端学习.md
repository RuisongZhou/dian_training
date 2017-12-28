* HTML 标题（Heading）是通过 <h1> - <h6> 等标签进行定义的。
* HTML 段落是通过 <p> 标签进行定义的。
* HTML 链接是通过 <a> 标签进行定义的
 <a href="http://www.w3school.com.cn">This is a link</a>
* HTML 图像是通过 <img> 标签进行定义的。
 <img border="0" src="/i/tulip_ballade.jpg" alt="Tulip">
* 属性值应该始终被包括在引号内。双引号是最常用的，不过使用单引号也没有问题。
在某些个别的情况下，比如属性值本身就含有双引号，那么您必须使用单引号，例如：
name='Bill "HelloWorld" Gates'
*  <hr /> 标签在 HTML 页面中创建水平线。
* <!--内容 -->	定义注释。
* <br /> 插入空行
* HTML 折行
* 如果您希望在不产生一个新段落的情况下进行换行（新行），请使用 <br /> 标签：
<p>This is<br />a para<br />graph with line breaks</p>

* text-align 属性规定了元素中文本的水平对齐方式
* font-family、color 以及 font-size 属性分别定义元素中文本的字体系、列颜色和字体尺寸
* 文本格式化标签

|标签		|描述		|
|:---------:|:-------:|
|```<b>```	|定义粗体文本。|
|```<big>```|	定义大号字。|
|```<em>```|	定义着重文字。|
|```<i>```|	定义斜体字。|
|```<small>```|	定义小号字。|
|```<strong>```|	定义加重语气。|
|```<sub>```|	定义下标字。|
|```<sup>```|	定义上标字。|
|```<ins>```|	定义插入字。|
|```<del>```|	定义删除字。|

* 计算机输出标签

|标签	|描述|
|:--------:|:-------:|
|```<code>```	|定义计算机代码。|
|```<kbd>```	|定义键盘码。|
|```<samp>```	|定义计算机代码样本。|
|```<tt>```	|定义打字机代码。|
|```<var>```|	定义数学变量。|
|```<pre>```|	定义预格式文本。|

* HTML ```<q>``` 元素定义短的引用。浏览器通常会为 ```<q>``` 元素包围引号。
	<p>WWF 的目标是：<q>构建人与自然和谐共存的世界。</q></p>
* HTML <blockquote> 元素定义被引用的节。
浏览器通常会对 <blockquote> 元素进行缩进处理
	<p>以下内容引用自 WWF 的网站：</p>
<blockquote cite="http://www.worldwildlife.org/who/index.html">
五十年来，WWF 一直致力于保护自然界的未来。
世界领先的环保组织，WWF 工作于 100 个国家，
并得到美国一百二十万会员及全球近五百万会员的支持。
</blockquote>
* HTML <abbr> 元素定义缩写或首字母缩略语。
对缩写进行标记能够为浏览器、翻译系统以及搜索引擎提供有用的信息。
<p><abbr title="World Health Organization">WHO</abbr> 成立于 1948 年。</p>
* HTML <dfn> 元素定义项目或缩写的定义。
	1. 如果设置了 <dfn> 元素的 title 属性，则定义项目。
		<p><dfn title="World Health Organization">WHO</dfn> 成立于 1948 年。</p>
		和<abbr>一样
	2. 如果 <dfn> 元素包含具有标题的 <abbr> 元素，则 title 定义项目。
		<p><dfn><abbr title="World Health Organization">WHO</abbr></dfn> 成立于 1948 年。</p>
	3. 否则，<dfn> 文本内容即是项目，并且父元素包含定义。
		<p><dfn>WHO</dfn> World Health Organization 成立于 1948 年。</p>
* HTML <address> 元素定义文档或文章的联系信息（作者/拥有者）。
此元素通常以斜体显示。大多数浏览器会在此元素前后添加折行。
<address>
Written by Donald Duck.<br> 
Visit us at:<br>
Example.com<br>
Box 564, Disneyland<br>
USA
</address>
* HTML <bdo> 元素定义双流向覆盖（bi-directional override）。
<bdo> 元素用于覆盖当前文本方向
	<bdo dir="rtl">This text will be written from right to left</bdo>
	会从右向左输出
* HTML <var> 元素定义数学变量
	<p>Einstein wrote:</p>
    <p><var>E = m c<sup>2</sup></var></p>
 * 条件注释
 <!--[if IE 8]>
    .... some HTML here ....
<![endif]-->
条件注释定义只有 Internet Explorer 执行的 HTML 标签。
* 样式
	1. 外部样式表
		当样式需要被应用到很多页面的时候，外部样式表将是理想的选择。使用外部样式表，你就可以通过更改一个文件来改变整个站点的外观。
			<head>
			<link rel="stylesheet" type="text/css" href="mystyle.css">
			</head>
	2.内部样式表
		当单个文件需要特别样式时，就可以使用内部样式表。你可以在 head 部分通过 <style> 标签定义内部样式表。
			<head>
			<style type="text/css">
			body {background-color: red}
			p {margin-left: 20px}
			</style>
			</head>
	3. 内联样式
		当特殊的样式需要应用到个别元素时，就可以使用内联样式。 使用内联样式的方法是在相关的标签中使用样式属性。样式属性可以包含任何 CSS 属性。以下实例显示出如何改变段落的颜色和左外边距。
			<p style="color: red; margin-left: 20px">
			This is a paragraph
			</p>
* HTML链接语法<a href="url">Link text</a>
  新窗口打开<a href="http://www.w3school.com.cn/" target="_blank">Visit W3School!</a>
* name属性<a name="label">锚（显示在页面上的文本）</a>
首先，我们在 HTML 文档中对锚进行命名（创建一个书签）：
<a name="tips">基本的注意事项 - 有用的提示</a>
然后，我们在同一个文档中创建指向该锚的链接：
<a href="#tips">有用的提示</a>
您也可以在其他页面中创建指向该锚的链接：
<a href="http://www.w3school.com.cn/html/html_links.asp#tips">有用的提示</a>
在上面的代码中，我们将 # 符号和锚名称添加到 URL 的末端，就可以直接链接到 tips 这个命名锚了。
* 跳出框架 <a href="/index.html" target="_top">请点击这里！</a> 
* 图像标签（<img>）和源属性（Src）
	定义图像的语法是：
	<img src="url" />
* 替换文本属性（Alt）
alt 属性用来为图像定义一串预备的可替换的文本。替换文本属性的值是用户定义的。
<img src="boat.gif" alt="Big Boat">
* 背景图片 <body background="/i/eg_background.jpg"></body>
* <img src ="/i/eg_cute.gif" align ="left"> 
带有图像的一个段落。图像的 align 属性设置为 "left"。图像将浮动到文本的左侧。
* <map>	定义图像地图。
<area>	定义图像地图中的可点击区域。
