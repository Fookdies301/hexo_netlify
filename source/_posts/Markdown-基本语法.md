---
title: Markdown 基本语法
tags:
  - Markdown语法
categories:
  - Markdown
abbrlink: '7894e390'
date: 2019-01-05 19:39:29
---
# Markdown 基本语法

## 段落

非常自然，一行文字就是一个段落。

比如

<h1>
```
这是一个段落。
```
</h1>


会被解释成

<h1>
```
<p>这是一个段落。</p>
```
</h1>


如果你需要另起一段，请在两个段落之间隔一个空行。

```
这是一个段落。

这是另一个段落。
```

会解释成

```
<p>这是一个段落<p>
<p>这是另一个段落</p>
```

不隔一个空行的换行行为，在一些编辑器中被解释为换行，即插入一个`<br />`标签。对与另外一些编辑器，会被解释为插入一个空格。对于后者，若要插入换行标签，请在当前一行的结尾打两个空格。

## 粗体、斜体

可以使用星号`*`或下划线`_`指定粗体或者斜体。

```
*这是斜体*
_这也是斜体_
**这是粗体**
***这是粗体+斜体***
```

会被解释成

```
<em>这是斜体</em>
<em>这也是斜体</em>
<strong>这是粗体</strong>
<strong><em>这是粗体+斜体</strong></em>
```

## 删除线

一部分编辑器支持删除线，它不是经典markdown中的要素。用波浪线`~`定义删除线。

```
~~就像这样~~
```

会被解释成

```
<strike>就像这样</strike>
```

## 标题

markdown总支持1~6六级标题，通过在一行之前加上不同数量的井号来表示。

```
# 这是 H1 #

## 这是 H2 ##

### 这是 H3 ###

...

###### 这是 H6 ######
```

行尾可以加上任意数量的井号字符，这些字符不会算作标题内容。通常会加上相等数量的字符以保持对称。

此外，H1和H2也可以采用在文本下方添加底线来实现，比如：

```
这是 H1
=======

这是 H2
-------
```

## 引用

通过在行首加上大于号`>`来添加引用格式。

```
> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.

> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
id sem consectetuer libero luctus adipiscing.
```

引用可以嵌套：

```
> This is the first level of quoting.
>
> > This is nested blockquote.
>
> Back to the first level.
```

也可以嵌套其他格式：

```
> ## 这是一个标题。
>
> 1.   这是第一行列表项。
> 2.   这是第二行列表项。
>
> 给出一些例子代码：
>
>     return shell_exec("echo $input | $markdown_script");
```

## 列表

无序列表使用星号、加号或是减号作为列表标记：

```
*   Red
*   Green
*   Blue
```

等同于

```
+   Red
+   Green
+   Blue
```

和

```
-   Red
-   Green
-   Blue
```

有序列表则使用数字接着一个英文句点：

```
1.  Bird
2.  McHale
3.  Parish
```

数字并不会影响输出的 HTML 结果，也就是说上面的例子等同于：

```
1.  Bird
1.  McHale
1.  Parish
```

## 内联代码

用反引号`` ` ``来标记内联代码，它们会解释成`<code>`标签。如果代码的内容中有反引号，请用两个反引号包裹。代码中的`&`、`<`、`>`符号都会自动转义，请放心使用。

## 代码区域

有两种方式标记代码区域，原生风格是行首缩进四个空格。

```
这是一个普通段落：

    这是一个代码区块。
```

会被解释成

```
<p>这是一个普通段落：</p>

<pre><code>这是一个代码区块。
</code></pre>
```

除了行首的4个空格会被移出，其它不变。像内联代码一样，上述三种符号也会被转义。但在代码段中，星号之类的markdown标记符号则不会解析。

还有一种是github的风格，代码段的前后用三个反引号独占一行来标记。

![](https://raw.githubusercontent.com/Fookdies301/markdown-simple-world/master/img/2-1.png)

目前主流编辑器都支持这种风格。

## 分隔线

你可以在一行中用三个以上的星号、减号、底线来建立一个分隔线，行内不能有其他东西。你也可以在星号或是减号中间插入空格。下面每种写法都可以建立分隔线：

```
* * *
***
*****
- - -
---------------------------------------
```

## 链接

```
[an example](http://example.com/)
[an example](http://example.com/ "Optional Title")
```

会被解释为

```
<a href='http://example.com/'>an example</a>
<a href='http://example.com/' title="Optional Title">an example</a>
```

除了上面的行内式，也可以使用参考式：

```
[an example][id]
```

然后在任意空白位置定义：

```
[id]: http://example.com/ "Optional Title"
```

## 图像

```
![Alt text](/path/to/img.jpg)
![Alt text](/path/to/img.jpg "Optional Title")
```

会被解释为

```
<img src='/path/to/img.jpg' alt='Alt text' />
<img src='/path/to/img.jpg' alt='Alt text' title='Optional Title' />
```

同样，图像也有类似的参考式语法。

## 自动链接

如果链接的地址和名字重复，可以用尖括号语法将其简化。

```
<http://example.com/>
```

就相当于

```
[http://example.com/](http://example.com/)
```

切记，大多数编辑器都会自动将符合url规则的东西视为链接，并且解释成链接。很多时候作者由于疏忽等缘故，链接和后面的中文之间缺少空格，导致链接不正常。所以我建议，链接要么加上尖括号，要么两端加上空格。

## 转义

markdown支持在以下字符前面插入反斜杠

```
\   反斜线
`   反引号
*   星号
_   底线
{}  花括号
[]  方括号
()  括弧
#   井字号
+   加号
-   减号
.   英文句点
!   惊叹号
```

插入之后，将不再解析这些字符，而是原样输出。

## 表格

表格是github风格独有的语法，但近年来渐渐被大多数编辑器支持。

```
| Item     | Value | Qty   |
| :------- | ----: | :---: |
| Computer | $1600 |  5    |
| Phone    | $12   |  12   |
| Pipe     | $1    |  234  |
```

会被解释成

```
<table>
<thead>
<tr>
  <th align="left">Item</th>
  <th align="right">Value</th>
  <th align="center">Qty</th>
</tr>
</thead>
<tbody><tr>
  <td align="left">Computer</td>
  <td align="right">$1600</td>
  <td align="center">5</td>
</tr>
<tr>
  <td align="left">Phone</td>
  <td align="right">$12</td>
  <td align="center">12</td>
</tr>
<tr>
  <td align="left">Pipe</td>
  <td align="right">$1</td>
  <td align="center">234</td>
</tr>
</tbody></table>
```

要注意第二行的冒号决定了居左居右还是居中，如果你不加冒号，默认是居左的。

另外可以把第一行去掉，做成没有表头的表格，但第二行始终是要有的。

## 内联 HTML

markdown 的语法简洁，但有其局限性，所以特意保留了内联html这种方式。任何html标签及其内容，都会原样输出到结果中。也就是说，标签中的星号等作为markdown结构的符号，以及构成html标签和实体的符号，都不会做任何转义。


# Markdown 高级语法

只有少数编辑器支持，使用前请先确认。

## 定义列表

```
Term 1
Term 2
:   Definition A
:   Definition B
```

会被编译成

```
<dl>
<dd>Term 1</dd>
<dd>Term 2</dd>
<dt>Definition A<dt>
<dt>Definition A<dt>
</dl>
```

## 目录

通过`[TOC]`标记来插入目录。

在编辑器不支持`[TOC]`标记的情况下可以使用添加id的方法构建目录。

```
### Directory
* [1.Content one](#chapter1)
* [2.Content two](#chapter2)

### <span id="chapter1">1.Content one</span>

### <span id="chapter2">2.Content two</span>
```


## TeX公式

内联的TeX公式使用一个美元符号标记。

```
$\Gamma(n) = (n-1)!\quad\forall n\in\mathbb N$
```

会被编译成

![](https://raw.githubusercontent.com/Fookdies301/markdown-simple-world/master/img/3-1.png)

TeX公式块用独占一行的两个美元符号来标记。

```
$$
\Gamma(z) = \int_0^\infty t^{z-1}e^{-t}dt\,.
$$
```

会被编译成

![](https://raw.githubusercontent.com/Fookdies301/markdown-simple-world/master/img/3-2.png)

如果你的编辑器不支持这个功能，可以手动解决。首先引入mathjax脚本：

```
<script type="text/javascript" src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS_HTML"></script>
```

之后，在需要插入公式的地方使用`<script>`标签包裹公式：

```
<script type="math/tex">\Gamma(n) = (n-1)!\quad\forall n\in\mathbb N</script>

<script type="math/tex; mode=display">
\Gamma(z) = \int_0^\infty t^{z-1}e^{-t}dt\,.
</script>
```

TeX的语法参考请见[这里](http://meta.math.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference)。

## UML图

可以像这样来画uml时序图：

![](https://raw.githubusercontent.com/Fookdies301/markdown-simple-world/master/img/3-3.png)

![](https://raw.githubusercontent.com/Fookdies301/markdown-simple-world/master/img/3-4.png)

这是uml流程图：

![](https://raw.githubusercontent.com/Fookdies301/markdown-simple-world/master/img/3-5.png)

![](https://raw.githubusercontent.com/Fookdies301/markdown-simple-world/master/img/3-6.png)

时序图的语法请见[这里](http://bramp.github.io/js-sequence-diagrams/)。流程图的语法请见[这里](http://adrai.github.io/flowchart.js/)。

# markdown部分语法技巧1 -字体-换行-缩进
## 1.换行：

``` js
  方法1: 连续两个以上空格+回车
  方法2：使用html语言换行标签：<br>
```

## 2.首行缩进两个字符：(每个表示一个空格，连续使用两个即可）

``` js
  &ensp; 半角的空格(&#8194;)
  &emsp; 全角的空格(&#8195;)
  &nbsp; 不断行的空格(&#160;)
```

## 3.[字体、字号与颜色](http://blog.csdn.net/testcs_dn/article/details/45719357):

## &emsp;&emsp;Markdown是一种可以使用普通文本编辑器编写的标记语言，通过类似HTML的标记语法，它可以使普通文本内容具有一定的格式。但是它本身是不支持修改字体、字号与颜色等功能的！

## &emsp;&emsp;CSDN-markdown编辑器是其衍生版本，扩展了Markdown的功能（如表格、脚注、内嵌HTML等等）！对，就是内嵌HTML，接下来要讲的功能就需要使用内嵌HTML的方法来实现。

字体，字号和颜色编辑如下代码

``` java
<font face="黑体">我是黑体字</font>
<font face="微软雅黑">我是微软雅黑</font>
<font face="STCAIYUN">我是华文彩云</font>
<font color=#0099ff size=7 face="黑体">color=#0099ff size=72 face="黑体"</font>
<font color=#00ffff size=72>color=#00ffff</font>
<font color=gray size=72>color=gray</font>
 
Size：规定文本的尺寸大小。可能的值：从 1 到 7 的数字。浏览器默认值是 3
```

## 具体颜色分类及标记请参照：[各种颜色](http://blog.csdn.net/testcs_dn/article/details/45719357/)
## 4.[背景色](http://blog.csdn.net/testcs_dn/article/details/45766819)：

>## Markdown本身不支持背景色设置，需要采用内置html的方式实现：借助 table, tr, td 等表格标签的 bgcolor 属性来实现背景色的功能。举例如下：

``` bash

```
## 背景色

>``` java
<table><tr><td bgcolor=#FF4500>这里的背景色是：OrangeRed，  十六进制颜色值：#FF4500， rgb(255, 69, 0)</td></tr></table>
```

## 呈现效果如下

<table><tr><td bgcolor=#FF4500>这里的背景色是：OrangeRed，  十六进制颜色值：#FF4500， rgb(255, 69, 0)</td></tr></table>

```js

```

## 5.分割线：你可以在一行中用三个以上的星号、减号、底线来建立一个分隔线，行内不能有其他东西。你也可以在星号或是减号中间插入空格。下面每种写法都可以建立分隔线

## 6.链接：链接文字都是用 [方括号] 来标记,在方块括号后面紧接着圆括号并插入网址链接即可:可[参照](http://www.markdown.cn/#links) 
## [This link](http://example.NET/) has no title attribute.

## 7.[代码块](http://blog.csdn.net/testcs_dn/article/details/44204303)：

## &emsp;&emsp;1.代码块：用2个以上TAB键起始的段落，会被认为是代码块（效果如下）：
    struct {
      int year;
      int month;
      int day;
     }bdate;

## &emsp;&emsp;2.如果在一个行内需要引用代码，只要用反引号`引起来就好(Esc健）

## &emsp;&emsp;3.代码块与语法高亮：在需要高亮的代码块的前一行及后一行使用三个反引号“`”，同时第一行反引号后面表面代码块所使用的语言

## 8.[使用LaTex数学公式](http://blog.csdn.net/testcs_dn/article/details/44229085): 

## &emsp;&emsp;1.行内公式：使用两个”$”符号引用公式: $公式$
## &emsp;&emsp;2.行间公式：使用两对“$$”符号引用公式： $$公式$$ 


# 字体、字号与颜色

``` js
<font face="黑体">我是黑体字</font>
<font face="微软雅黑">我是微软雅黑</font>
<font face="STCAIYUN">我是华文彩云</font>
<font color=#0099ff size=7 face="黑体">color=#0099ff size=72 face="黑体"</font>
<font color=#00ffff size=72>color=#00ffff</font>
<font color=gray size=72>color=gray</font>
```

## Size：规定文本的尺寸大小。可能的值：从 1 到 7 的数字。浏览器默认值是 3。

## 呈现效果

<font face="黑体">我是黑体字</font>
<font face="微软雅黑">我是微软雅黑</font>
<font face="STCAIYUN">我是华文彩云</font>
<font color=#0099ff size=7 face="黑体">color=#0099ff size=72 face="黑体"</font>
<font color=#00ffff size=72>color=#00ffff</font>
<font color=gray size=72>color=gray</font>

# 颜色名列表

| 颜色名 | 十六进制颜色值 | 颜色 |
| :--------: | :-------: | :-----: |
| AliceBlue | #F0F8FF | rgb(240, 248, 255) |
| AntiqueWhite | #FAEBD7 | rgb(250, 235, 215) |
| Aqua | #00FFFF | rgb(0, 255, 255) |
| Aquamarine | #7FFFD4 | rgb(127, 255, 212) |
| Azure | #F0FFFF | rgb(240, 255, 255) |
| Beige | #F5F5DC | rgb(245, 245, 220) |
| Bisque | #FFE4C4 | rgb(255, 228, 196) |
| Black | #000000 | rgb(0, 0, 0) |
| BlanchedAlmond | #FFEBCD | rgb(255, 235, 205) |
| Blue | #0000FF | rgb(0, 0, 255) |
| BlueViolet | #8A2BE2 | rgb(138, 43, 226) |
| Brown | #A52A2A | rgb(165, 42, 42) |
| BurlyWood | #DEB887 | rgb(222, 184, 135) |
| CadetBlue | #5F9EA0 | rgb(95, 158, 160) |
| Chartreuse | #7FFF00 | rgb(127, 255, 0) |
| Chocolate | #D2691E | rgb(210, 105, 30) |
| Coral | #FF7F50 | rgb(255, 127, 80) |
| CornflowerBlue | #6495ED | rgb(100, 149, 237) |
| Cornsilk | #FFF8DC | rgb(255, 248, 220) |
| Crimson | #DC143C | rgb(220, 20, 60) |
| Cyan | #00FFFF | rgb(0, 255, 255) |
| DarkBlue | #00008B | rgb(0, 0, 139) |
| DarkCyan | #008B8B | rgb(0, 139, 139) |
| DarkGoldenRod | #B8860B | rgb(184, 134, 11) |
| DarkGray | #A9A9A9 | rgb(169, 169, 169) |
| DarkGreen | #006400 | rgb(0, 100, 0) |
| DarkKhaki | #BDB76B | rgb(189, 183, 107) |
| DarkMagenta | #8B008B | rgb(139, 0, 139) |
| DarkOliveGreen | #556B2F | rgb(85, 107, 47) |
| Darkorange |#FF8C00 | rgb(255, 140, 0) |
| DarkOrchid | #9932CC | rgb(153, 50, 204) |
| DarkRed | #8B0000 | rgb(139, 0, 0) |
| DarkSalmon| #E9967A | rgb(233, 150, 122) |
| DarkSeaGreen | #8FBC8F | rgb(143, 188, 143) |
| DarkSlateBlue | #483D8B | rgb(72, 61, 139) |
| DarkSlateGray | #2F4F4F | rgb(47, 79, 79) |
| DarkTurquoise | #00CED1 | rgb(0, 206, 209) |
| DarkViolet | #9400D3 | rgb(148, 0, 211) |
| DeepPink | #FF1493 | rgb(255, 20, 147) |
| DeepSkyBlue | #00BFFF | rgb(0, 191, 255) |
| DimGray | #696969 | rgb(105, 105, 105) |
| DodgerBlue | #1E90FF | rgb(30, 144, 255) |
| Feldspar | #D19275 | rgb(209, 146, 117) |
| FireBrick | #B22222 | rgb(178, 34, 34) |
| FloralWhite | #FFFAF0 | rgb(255, 250, 240) |
| ForestGreen | #228B22 | rgb(34, 139, 34) |
| Fuchsia | #FF00FF | rgb(255, 0, 255) |
| Gainsboro | #DCDCDC | rgb(220, 220, 220) |
| GhostWhite | #F8F8FF | rgb(248, 248, 255) |
| Gold | #FFD700 | rgb(255, 215, 0) |
| GoldenRod | #DAA520 | rgb(218, 165, 32) |
| Gray | #808080 | rgb(128, 128, 128) |
| Green| #008000 | rgb(0, 128, 0) |
| GreenYellow | #ADFF2F | rgb(173, 255, 47) |
| HoneyDew | #F0FFF0 | rgb(240, 255, 240) |
| HotPink | #FF69B4 | rgb(255, 105, 180) |
| IndianRed | #CD5C5C | rgb(205, 92, 92) |
| Indigo | #4B0082 | rgb(75, 0, 130) |
| Ivory | #FFFFF0 | rgb(255, 255, 240) |
| Khaki | #F0E68C | rgb(240, 230, 140) |
| Lavender | #E6E6FA | rgb(230, 230, 250) |
| LavenderBlush | #FFF0F5 | rgb(255, 240, 245) |
| LawnGreen | #7CFC00 | rgb(124, 252, 0) |
| LemonChiffon | #FFFACD | rgb(255, 250, 205) |
| LightBlue | #ADD8E6 | rgb(173, 216, 230) |
| LightCoral | #F08080 | rgb(240, 128, 128) |
| LightCyan | #E0FFFF | rgb(224, 255, 255) |
| LightGoldenRodYellow | #FAFAD2 | rgb(250, 250, 210) |
| LightGrey | #D3D3D3 | rgb(211, 211, 211) |
| LightGreen | #90EE90 | rgb(144, 238, 144) |
| LightPink | #FFB6C1 | rgb(255, 182, 193) |
| LightSalmon | #FFA07A | rgb(255, 160, 122) |
| LightSeaGreen | #20B2AA | rgb(32, 178, 170) |
| LightSkyBlue | #87CEFA | rgb(135, 206, 250) |
| LightSlateBlue | #8470FF | rgb(132, 112, 255) |
| LightSlateGray | #778899 | rgb(119, 136, 153) |
| LightSteelBlue | #B0C4DE | rgb(176, 196, 222) |
| LightYellow | #FFFFE0 | rgb(255, 255, 224) |
| Lime | #00FF00 | rgb(0, 255, 0) |
| LimeGreen | #32CD32 | rgb(50, 205, 50) |
| Linen | #FAF0E6 | rgb(250, 240, 230) |
| Magenta | #FF00FF | rgb(255, 0, 255) |
| Maroon | #800000 | rgb(128, 0, 0) |
| MediumAquaMarine | #66CDAA | rgb(102, 205, 170) |
| MediumBlue | #0000CD | rgb(0, 0, 205) |
| MediumOrchid | #BA55D3 | rgb(186, 85, 211) |
| MediumPurple | #9370D8 | rgb(147, 112, 216) |
| MediumSeaGreen | #3CB371 | rgb(60, 179, 113) |
| MediumSlateBlue | #7B68EE | rgb(123, 104, 238) |
| MediumSpringGreen | #00FA9A | rgb(0, 250, 154) |
| MediumTurquoise | #48D1CC | rgb(72, 209, 204) |
| MediumVioletRed | #C71585 | rgb(199, 21, 133) |
| MidnightBlue | #191970 | rgb(25, 25, 112) |
| MintCream | #F5FFFA | rgb(245, 255, 250) |
| MistyRose | #FFE4E1 | rgb(255, 228, 225) |
| Moccasin | #FFE4B5 | rgb(255, 228, 181) |
| NavajoWhite | #FFDEAD | rgb(255, 222, 173) |
| Navy | #000080 | rgb(0, 0, 128) |
| OldLace | #FDF5E6 | rgb(253, 245, 230) |
| Olive | #808000 | rgb(128, 128, 0) |
| OliveDrab | #6B8E23 | rgb(107, 142, 35) |
| Orange | #FFA500 | rgb(255, 165, 0) |
| OrangeRed | #FF4500 | rgb(255, 69, 0) |
| Orchid | #DA70D6 | rgb(218, 112, 214) |
| PaleGoldenRod | #EEE8AA | rgb(238, 232, 170) |
| PaleGreen | #98FB98 | rgb(152, 251, 152) |
| PaleTurquoise | #AFEEEE | rgb(175, 238, 238) |
| PaleVioletRed | #D87093 | rgb(216, 112, 147) |
| PapayaWhip | #FFEFD5 | rgb(255, 239, 213) |
| PeachPuff | #FFDAB9 | rgb(255, 218, 185) |
| Peru | #CD853F | rgb(205, 133, 63) |
| Pink | #FFC0CB | rgb(255, 192, 203) |
| Plum | #DDA0DD | rgb(221, 160, 221) |
| PowderBlue | #B0E0E6 | rgb(176, 224, 230) |
| Purple | #800080 | rgb(128, 0, 128) |
| Red | #FF0000 | rgb(255, 0, 0) |
| RosyBrown | #BC8F8F | rgb(188, 143, 143) |
| RoyalBlue | #4169E1 | rgb(65, 105, 225) |
| SaddleBrown | #8B4513 | rgb(139, 69, 19) |
| Salmon | #FA8072 | rgb(250, 128, 114) |
| SandyBrown | #F4A460 | rgb(244, 164, 96) |
| SeaGreen | #2E8B57 | rgb(46, 139, 87) |
| SeaShell | #FFF5EE | rgb(255, 245, 238) |
| Sienna | #A0522D | rgb(160, 82, 45) |
| Silver | #C0C0C0 | rgb(192, 192, 192) |
| SkyBlue | #87CEEB | rgb(135, 206, 235) |
| SlateBlue | #6A5ACD | rgb(106, 90, 205) |
| SlateGray | #708090 | rgb(112, 128, 144) |
| Snow | #FFFAFA | rgb(255, 250, 250) |
| SpringGreen | #00FF7F | rgb(0, 255, 127) |
| SteelBlue | #4682B4 | rgb(70, 130, 180) |
| Tan | #D2B48C | rgb(210, 180, 140) |
| Teal | #008080 | rgb(0, 128, 128) |
| Thistle | #D8BFD8 | rgb(216, 191, 216) |
| Tomato | #FF6347 | rgb(255, 99, 71) |
| Turquoise | #40E0D0 | rgb(64, 224, 208) |
| Violet | #EE82EE | rgb(238, 130, 238) |
| VioletRed | #D02090 | rgb(208, 32, 144) |
| Wheat | #F5DEB3 | rgb(245, 222, 179) |
| White | #FFFFFF | rgb(255, 255, 255) |
| WhiteSmoke | #F5F5F5 | rgb(245, 245, 245) |
| Yellow | #FFFF00 | rgb(255, 255, 0) |
| YellowGreen | #9ACD32 | rgb(154, 205, 50) |
