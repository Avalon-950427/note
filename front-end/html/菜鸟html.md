# 标题

- 标题标签是通过`<h1>-<h6>`来定义的
- 标题标签只用于标题,不仅仅是为了生成粗体和大号文本

# 段落

- `<p>`标签是段落标签,属于块级元素,浏览器会自动在段落标签前后加上空行

# 文本格式化

**HTML文本格式化标签**

| 标签       | 描述                                                         |
| ---------- | ------------------------------------------------------------ |
| `<b>`      | 定义粗体文字                                                 |
| `<strong>` | 定义粗体文字,有强调语义                                      |
| `<i>`      | 定义斜体文字                                                 |
| `<em>`     | 定义斜体文字,有强调语义                                      |
| `<sub>`    | 定义下标字                                                   |
| `<sup>`    | 定义上标字                                                   |
| `<ins>`    | 定义插入字,有下划线效果,与`<del>`一起使用,来描述文档中的更新和修正 |
| `<del>`    | 定义删除子,有中划线效果,与`<ins>`一起使用,来描述文档中的更新和修正 |

**HTML计算机输出标签**

| 标签     | 描述                   |
| -------- | ---------------------- |
| `<code>` | 定义计算机代码         |
| `<samp>` | 定义计算机代码输出样本 |
| `<var>`  | 定义变量               |
| `<pre>`  | 定义预格式文本         |

**HTML引用引文标签**

| 标签           | 描述                                                         |
| -------------- | ------------------------------------------------------------ |
| `<abbr>`       | 定义缩写,有下划虚线效果                                      |
| `<address>`    | 定义地址,有斜体效果。在`<body>` 元素内部，则它表示该文档作者/所有者的联系信息。在` <article> `元素内部，则它表示该文章作者/所有者的联系信息。 |
| `<bdo>`        | 定义文字方向。`dir`属性可定义方向,`ltr`属性值表示左到右,`rtl`表示右到左 |
| `<blockquote>` | 定义长的引用,引用的文本需要段落分割,元素四周有margin         |
| `<q>`          | 定义短的引用,元素四周的margin比`<blockquote>`小,且有双引号包裹 |
| `<cite>`       | 标签定义作品（比如书籍、歌曲、电影、电视节目、绘画、雕塑等等）的标题。有斜体效果 |
| `<dfn>`        | 定义一个项目。有斜体效果                                     |

# 链接元素

`a`标签用于定义从一个页面跳转到另一个页面的超链接

- 未被访问的链接带有下划线且是蓝色
- 已被访问的链接带有下划线且是紫色
- 激活状态下带有下划线且是红色

| 属性       | 描述                                                         |
| ---------- | ------------------------------------------------------------ |
| `download` | 指定了`href`之后再指定`download`属性,可以直接下载资源(同源资源) |
| `href`     | 规定链接的目标`url`                                          |
| `media`    | 规定目标`url`的媒介类型                                      |
| `target`   | 规定在何处打开目标`url`,可选值有`_blank,_parent,_self,_top`  |
| `type`     | 设置目标`url`的`MIME`类型                                    |

# 头部标签

## `<head>`元素

`<head>`元素包含所有头部标签元素,可在里面的标签有`<title>,<meta>,<base>,<link>,<style>,<script>,<noscript>`

## `<title>`元素

`<title>`元素定义了不同文档的标题:

- 定了浏览器工具栏的标题
- 定义了网页添加到收藏夹时的标题
- 显示在搜索引擎结果页面的标题

## `<base>`元素

`<base>`标签描述基本的链接地址,该标签作为HTML文档所有`<a>`标签的默认链接

## `<link>`元素

用于引入外部资源

## `<meta>`元素

描述了一些基本元数据

```html
为搜索引擎定义关键字
<meta name="keywords" content="HTML,css,js"
```

```html
为网页定义描述内容
<meta name="description" content="免费 Web & 编程 教程">
```

```
定义网页作者
<meta name="author" content="Runoob">
```

# 图像元素

| 属性     | 描述                       |
| -------- | -------------------------- |
| `src`    | 指定图像路径               |
| `alt`    | 指定图像可替换文本         |
| `width`  | 指定图像宽度               |
| `height` | 指定图像高度               |
| `ismap`  | 将图像规定为服务端图像映射 |
| `usemap` | 将地图规定为客户端图像映射 |

```html
<img src="planets.gif" width="145" height="126" alt="Planets" usemap="#planetmap">

<map name="planetmap">
  <area shape="rect" coords="0,0,82,126" alt="Sun" href="sun.htm">
  <area shape="circle" coords="90,58,3" alt="Mercury" href="mercur.htm">
  <area shape="circle" coords="124,58,8" alt="Venus" href="venus.htm">
</map>
```

# 表格元素

## `<table>`元素

`<table>`元素定义HTML表格

| 属性          | 描述                                     |
| ------------- | ---------------------------------------- |
| `border`      | 定义表格边框,只支持1(有边框)和""(没边框) |
| `cellspacing` | 定义表格单元格之间间距                   |
| `cellpadding` | 定义表格单元格的内边距                   |

## `<th>`元素

`<th>`元素是表头单元格

| 属性      | 描述                   |
| --------- | ---------------------- |
| `colspan` | 规定单元格可横跨的列数 |
| `rowspan` | 规定单元格可横跨的行数 |

## `<tr>`元素

定义表格中的行

## `<td>`元素

定义表格的单元格

| 属性      | 描述                   |
| --------- | ---------------------- |
| `colspan` | 规定单元格可横跨的列数 |
| `rowspan` | 规定单元格可横跨的行数 |

## `<caption>`元素

定义表格的标题

## `<colgroup>`和`<col>`元素

`<colgroup>`定义表格列的组,`<col>`定义用于表格列的属性

**`<col>`元素属性**

| 属性   | 描述                   |
| ------ | ---------------------- |
| `span` | 规定列组应该横跨的行数 |

```html
<table border="1">
  <colgroup>
    <col span="2" style="background-color:red"> <!--前两列为一个组-->
    <col style="background-color:yellow"> <!--第三列为一个组-->
  </colgroup>
  <tr>
    <th>ISBN</th>
    <th>Title</th>
    <th>Price</th>
  </tr>
  <tr>
    <td>3476896</td>
    <td>My first HTML</td>
    <td>$53</td>
  </tr>
</table>
```

## `<thead>`元素

`<thead>`元素用于定义页眉,该元素一定处于`<table>`标签第一行

```html
<thead>
    <tr>
      <th>Month</th>
      <th>Savings</th>
    </tr>
  </thead>
```

## `<tbody>`元素

用于定义表格主体内容

## `<tfoot>`元素

用于定义表格的页脚,一定处于`<table>`元素的最后一行

# 列表

## 无序列表

```html
<ul>
	<li>xxx</li>
</ul>
```

## 有序列表

```html
<ol>
    <li>xxx</li>
</ol>
```

## 自定义列表

```html
<dl>
    <dt>coffie
        <dd>333</dd>
        <dd>333</dd>
    </dt>
    <dt>jjj
        <dd>kkk</dd>
    </dt>
</dl>
```

# 表单

## `<form>`元素

| 属性             | 值                                                           | 描述                                       |
| ---------------- | ------------------------------------------------------------ | ------------------------------------------ |
| `accept`         | MIME_TYPE                                                    | 规定服务器接收到的文件的类型               |
| `accept-charset` | character_set                                                | 规定服务器可处理的表单数据字符集           |
| `action`         | URL                                                          | 规定表单提交时向何处发送表单数据           |
| `autocomplete`   | on/off                                                       | 规定是否启用表单的自动完成功能             |
| `enctype`        | `application/x-www-form-urlencoded`,`multipart/form-data`,`text/plain` | 规定在向服务器发送表单数据之前如何对其编码 |
| `method`         | get/post                                                     | 规定用于发送表单数据的HTTP方法             |
| `name`           | text                                                         | 规定表单的名称                             |
| `novalidate`     | `novalidate`                                                 | 如果使用该属性,则提交表单时不进行验证      |
| `target`         | `_blank`,`_self`,`_parent`,`_top`                            | 规定在如何打开`action URL`                 |

# 框架

| 属性     | 描述                        |
| -------- | --------------------------- |
| `src`    | 规定在框架中显示的文档的URL |
| `width`  | 规定框架的宽度              |
| `height` | 规定框架的高度              |
| `name`   | 规定框架的名称              |

```html
动态指定框架src
<iframe src="demo_iframe.htm" name="iframe_a"></iframe>
<p><a href="http://www.runoob.com" target="iframe_a">RUNOOB.COM</a></p>
```

