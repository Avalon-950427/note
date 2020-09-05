# css规则组成

![]()![css-ruler](E:\note\front-end\images\css-ruler.png)

# 背景

## `background-color`

`background-color`:定义背景颜色

## `background-image`

`background-image`:定义背景图片,取值为`none`和`url()`

## `background-repeat`

`background-repeat`:定义背景平铺

| 属性值     | 描述                                                         |
| ---------- | ------------------------------------------------------------ |
| `repeat-x` | 水平平铺                                                     |
| `repeat-y` | 垂直平铺                                                     |
| `space`    | 会自适应调整图片大小,不会去裁剪图片,多个存不下会省略一个,且`background-position`会被忽略, |
| `round`    | 当多个背景图片存放不下时,会平分空间,各自等比缩小             |

## `background-attachment`

`background-attachment`决定背景图片的位置是在视口内固定还是随着父元素滚动

| 属性值   | 描述                     |
| -------- | ------------------------ |
| `fixed`  | 背景相对于视口固定       |
| `local`  | 背景相对于元素的内容固定 |
| `scroll` | 背景相对于元素本身固定   |

## `background-position`

`background-position`:定义背景位置

## `background-origin`

`background-origin`:指定背景图片的`background-position`的相对位置

如果`background-attachment`值为`fixed`,那么此属性将没有效果

| 属性值        | 描述                              |
| ------------- | --------------------------------- |
| `padding-box` | 背景图片位置从padding区域开始指定 |
| `content-box` | 背景图片位置从内容区域开始指定    |
| `border-box`  | 背景图片位置从边框区域开始指定    |

## `background`

# 文本属性

## `color`

设置文本颜色

## `direction`

指定文本方向

## `letter-spacing`

指定字符间距

## `line-height`

设置行高

## `text-align`

设置文本对齐方式,值为left,right,center,justify

## `text-decoration`

设置下划线

| 属性值         | 描述   |
| -------------- | ------ |
| `overline`     | 上划线 |
| `line-through` | 中划线 |
| `underline`    | 下划线 |

## `text-indent`

设置首航缩进

## `text-shadow`

`text-shadow:x y 模糊半径 color`设置文本阴影,

## `text-transform`

设置字母大小写

| 属性值       | 描述           |
| ------------ | -------------- |
| `capitalize` | 单词首字母大写 |
| `uppercase`  | 字母大写       |
| `lowercase`  | 字母小写       |

## `vertical-align`

设置元素垂直方式

## `word-spacing`

设置单词间距

# 字体

## `font-family`

`font-family`属性设置字体

## `font-style`

设置字体倾斜

## `font-size`

设置字体大小

## `font-weight`

设置字重

# 链接伪类

## `a:link`

正常未访问过的状态

## `a:visited`

已访问过的状态

## `a:hover`

鼠标放在链接上

# 列表样式

## `list-style-type`

设置列表项标志的类型

## `list-style-image`

设置列表项标志图片

## `list-style-position`

设置表项标志位置

# Display

## display和visibility

`display:none`:隐藏元素,且不占用任何空间

`visibility:hidden`:隐藏元素,还是占用空间

## 块和内联元素

`display:block`:设置块元素

`display:inline`:设置内联元素

# 定位

## `static`定位

HTML元素的默认值,即没有定位,遵循正常的文档流

## `fixed`定位

元素的位置相对于浏览器窗口是固定位置

## `relative`定位

相对定位是相对其正常位置,其原本所占的空间不会改变

## `absolute`定位

绝对定位是相对于最近的已定位父元素,如果没有已定位的父元素,则相对于`<html>`元素

## `sticky`定位

粘性定位行为是`relative`和`fixed`的结合,当页面滚动超出目标区域时,就会显示固定定位

## `z-index`

定位元素可以指定层级来指定元素的堆叠顺序

