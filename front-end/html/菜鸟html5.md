# HTML5浏览器支持

## 为HTML添加新元素

虽然主流浏览器都支持HTML5,但不支持的浏览器会将无法识别的元素处理为内联元素。为了能最大化兼容,可以设置`css`的`display:block`

```html
header,section,footer,aside,nav,main,article,figure{
	display: block
}
```

## 为HTML添加新元素

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="utf-8"> 
        <title>为 HTML 添加新元素</title>
        <script>
        document.createElement("myHero")
        </script>
        <style>
        myHero {
            display: block;
            background-color: #ddd;
            padding: 50px;
            font-size: 30px;
        }
        </style> 
    </head>
    <body>
        <h1>我的第一个标题</h1>
        <p>我的第一个段落。</p>
        <myHero>我的第一个新元素</myHero>
    </body>
</html>
```

# canvas

## 创建画布

`<canvas>`标签只是图形容器,需要使用脚本来绘制图形

```html
<canvas id="myCanvas" width="200" height="100"style="border:1px solid #000000;"><!--canvas标签默认没有边框和内容-->
</canvas>
```

```js
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.fillStyle="#FF0000";
ctx.fillRect(0,0,150,75); // fillRect(x,ywidth,height)
```

## canvas路径

- `moveTo(x,y)`:定义线条开始坐标
- `lineTo(x,y)`:定义线条结束坐标

```js
// 绘制线条
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.moveTo(0,0);
ctx.lineTo(200,100);
ctx.stroke();
```

```js
// 绘制圆形
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.beginPath();
ctx.arc(95,50,40,0,2*Math.PI); // arc(x,y,r,start,stop)
ctx.stroke();
```

## canvas文本

使用`canvas`绘制文本,属性如下:

- font:定义字体和字体大小

- `fillText(text,x,y)`:在canvas上绘制实心文本
- `strokeText(text,x,y)`:在canvas上绘制空心文本

```js
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
ctx.font="30px Arial";
ctx.fillStyle="red";
ctx.strokeText("Hello World",10,50);
```

## canvas渐变

### 线性渐变

- `createLinearFradient(x,y,x1,y1)`:创建线性渐变,前两个参数是渐变开始坐标,后两个参数是渐变结束坐标
- `addColorStop(position,color)`:表示渐变色所在的位置,position必须是0到1中的数值

```js
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
 
// 创建渐变
var grd=ctx.createLinearGradient(0,0,200,0);
grd.addColorStop(0,"red");
grd.addColorStop(1,"white");
 
// 填充渐变
ctx.fillStyle=grd;
ctx.fillRect(10,10,150,80);
```

### 径向渐变

- `createRadialGradient(x1, y1, r1, x2, y2, r2) `:创建一个径向/圆渐变。接受 6 个参数，前三个定义一个以 (x1,y1) 为原点，半径为 r1 的圆，后三个参数则定义另一个以 (x2,y2) 为原点，半径为 r2 的圆。

```js
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
 
// 创建渐变
var grd=ctx.createRadialGradient(75,50,5,90,60,100);
grd.addColorStop(0,"red");
grd.addColorStop(1,"white");
 
// 填充渐变
ctx.fillStyle=grd;
ctx.fillRect(10,10,150,80);
```



## canvas图像

将一幅图像放置到画布上,使用`drawImage(image,x,y)`方法

```js
var c=document.getElementById("myCanvas");
var ctx=c.getContext("2d");
var img=document.getElementById("scream"); // 获取图像DOM
ctx.drawImage(img,10,10); // x,y是图像左上角位置
```

# 地理位置

- navigator.geolocation.getCurrentLocation(数据处理回调函数,错误处理回调函数): 获取当前位置

```js
function getLocation()
{
	if (navigator.geolocation)
	{
		navigator.geolocation.getCurrentPosition(showPosition,showError);
	}
	else
	{
		x.innerHTML="该浏览器不支持定位。";
	}
}
function showPosition(position)
{
	x.innerHTML="纬度: " + position.coords.latitude + 
	"<br>经度: " + position.coords.longitude;	
}
function showError(error)
{
	switch(error.code) 
	{
		case error.PERMISSION_DENIED:
			x.innerHTML="用户拒绝对获取地理位置的请求。"
			break;
		case error.POSITION_UNAVAILABLE:
			x.innerHTML="位置信息是不可用的。"
			break;
		case error.TIMEOUT:
			x.innerHTML="请求用户地理位置超时。"
			break;
		case error.UNKNOWN_ERROR:
			x.innerHTML="未知错误。"
			break;
	}
}
```



# HTML5语义元素

![](E:\note\front-end\images\语义化标签.png)

## `<section>`元素

`<section>`标签定义了文档中的章节、主题分组

## `<article>`元素

`<article>`标签指独立的包含内容。可从网站的其他部分独立阅读

## `<header>`元素

`<header>`元素描述文档头部区域,指定为一个文件或部分标题

## `<footer>`元素

`<footer>`元素描述文档底部区域,指定为一个文件或部分页脚

## `<nav>`元素

`<nav>`元素定义了一组导航链接

## `<aside>`元素

`<aside>`元素定义页面主区域内容之外的内容（比如侧边栏）。

## `<figure>`和`<figcaption>`

`<figure>`标签规定独立的流内容（图像、图表、照片、代码等等）。

`<figcaption>` 标签定义` <figure>` 元素的标题.

`<figcaption>`元素应该被置于 "figure" 元素的第一个或最后一个子元素的位置。

# HTML5新标签

## `<mark>`标签

定义带有记号的文本,默认是黄色的

## `<meter>`标签

`<meter>` 标签定义度量衡。仅用于已知最大和最小值的度量。

| 属性      | 描述                     |
| --------- | ------------------------ |
| `high`    | 规定被界定为高的值的范围 |
| `low`     | 规定被界定为低的值的范围 |
| `max`     | 规定范围的最大值         |
| `min`     | 规定范围的最小值         |
| `optimum` | 规定度量的最优值         |
| value     | 必须,规定度量的当前值    |

## `<progress>`标签

`<progress> `标签定义运行中的任务进度（进程）。需与js一起使用

| 属性    | 描述             |
| ------- | ---------------- |
| `max`   | 规定需要完成的值 |
| `value` | 规定进程的当前值 |

```js
<progress id='progress1' value="0" max="100"></progress>
<button onclick="start_run(100)">下载</button>

<script>
    function start_run(n)
    {
        if(n==0){
        	alert("下载完成")
        }else{
            var progress1=document.getElementById("progress1")
            n=n-1
            cur_task=100-n
            progress1.value=cur_task
            setTimeout("start_run("+n+")",100)
		}
    }
</script>
```

## `<time>`标签

该元素用来定义时间和日期

| 属性       | 描述                                          |
| ---------- | --------------------------------------------- |
| `datetime` | 规定时间/日期,如`datetime="2014-05-20 13:14"` |
| `pubdate`  | 表示文档的发布日期                            |

# HTML5存储

客户端存储数据的两个对象为:

- `localStorage`:用于长久保存整个网站的数据，保存的数据没有过期时间，直到手动去除。
- `sessionStorage`:用于临时保存同一窗口(或标签页)的数据，在关闭窗口或标签页之后将会删除这些数据。

```js
// 在使用 web 存储前,应检查浏览器是否支持 localStorage 和sessionStorage:
if(typeof(Storage)!=="undefined")
{
    // 是的! 支持 localStorage  sessionStorage 对象!
    // 一些代码.....
} else {
    // 抱歉! 不支持 web 存储。
}
```

**`localStorage`和`sessionStorage`可用的API都一样:**

- `localStorage.setItem(key,value)`:保存数据
- `localStorage.getItem(key)`:读取数据
- `localStorage.removeItem(key)`:删除单个数据
- `localStorage.clear()`:删除所有数据
- `localStorage.key(index)`:得到某个索引的key

# HTML5 Web SQL

- openDatabase('数据库名称','版本号','描述文件',数据库大小,创建回调):使用已有的数据库或者新建的数据库创建一个数据库对象
- transaction(回调函数):这个方法能控制一个事务,以及基于这种情况执行提交或者回滚
- executeSql(sql语句):用于执行实际的SQL查询

# Web Worker

- `new Worker(子线程文件)`:创建worker对象
- `postMessage()`:子线程向父线程传递数据
- `worker.onmessage`:父线程接收子线程的数据
- `worker.terminate()`:终止子线程

`web worker`位于外部文件中,所以无法访问`js`的`window对象`,`document对象`,`parent对象`

