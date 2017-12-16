``` javascript 
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
```
* text-align 属性规定了元素中文本的水平对齐方式
* font-family、color 以及 font-size 属性分别定义元素中文本的字体系列、颜色和字体尺寸
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
 *条件注释