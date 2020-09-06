# webpack常用知识

## webpack配置less

```shell
npm install less-loader less --save-dev
```

## webpack设置css模块化

作用是使js能直接使用模块.类名来设置元素的样式

```js
use:[
	{
		loader: 'css-loader',
		options: {
			modules: true // 开启css模块化
		}
	}
]
```

```css
/*index.css*/
ele{
	background: white
}
```

```js
// index.js
import css from 'index.css'

let ele = `<div class=${css.ele}>css module</div>`

document.write(ele)
```

## webpack设置postcss(css后处理器)

安装postcss-loader和自动加前缀插件,postcss-loader必须在css-loader之后使用

```shell
npm i postcss-loader autoprefixer -D
```

```js
// postcss.config.js
const autoprefixer = require('autoprefixer')
module.exports = {
  plugins: [
    autoprefixer({
      overrideBrowserslist: ["last 2 versions",">1%"] // 第一个参数兼容所有浏览器最近两个版本,第二个参数表示兼容全球浏览器份额>1%的浏览器
    })
  ]
}
// webpack.config.js
{
   		test: /\.less$/,
        use: [
            'style-loader', 
            {
                loader: 'css-loader',
                options:{
                    // 开启css模块化
                    modules: true
                }
            },
            {
                loader: 'postcss-loader'
            },
            'less-loader'
        ]
}
```

## webpack处理静态资源

file-loader处理静态资源模块,原理是把打包入口中识别出的资源模块,移动到输出目录,并且返回一个地址名称

url-loader:是file-loader的增强版,用法和file-loader一致,可以加limit限制资源大小,小于资源大小限制的,会编译成base64打包进bundle文件中

```js
{
  test: /.(png | jpe?g | gif)$/,
  use: {
    loader: 'file-loader',
    options: {
      name: '[name]-[hash:6].[ext]',
      outputPath: "images/" // 这样会在打包后资源文件引用路径上自动添加这个路径前缀
    }
  }
}
```

## webpack处理html页面

```
// webpack.config.plugin
const HtmlWebpackPlugin = require('html-webpack-plugin')

 plugins: [
    new HtmlWebpackPlugin({
      title:'首页',
      // 选择html模板,以这个html为模板输出到dist目录
      template: './src/index.html',
      // 输出的文件名
      filename: 'index.html'
    })
  ]
```

## sourceMap

源代码与打包后的代码的映射关系，通过sourceMap定位到源代码。
在dev模式中，开发模式下默认开启，关闭的话 可以在配置⽂文件⾥里里

```js
devtool:"none" // 关闭
devtool: 'source-map' // 开启source-map,生成.map文件
devtool: 'cheap-inline-source-map' // 只显示错误行数,不显示列数,且把映射放在bundle文件中

devtool: 'cheap-module-eval-source-map' // 开发环境配置
devtool: 'cheap-module=source-map' // 线上环境配置,不推荐开启
```

## mini-css-extract-plugin

```js
const MiniCssExtractPlugin = require("mini-css-extract-plugin");
{  
	test: /\.css$/,  
	use: [
		MiniCssExtractPlugin.loader, //这里因为需要抽离css,所以不需要style-loader
		"css-loader"
	] 
}

plugins:{
	new MiniCssExtractPlugin({   
        filename: "css/[name][chunkhash:8].css" 
   	})
}
```

# webpack-dev-server

可提升开发效率,用dev-server就不用每次改完代码都要去build以下,浏览器刷新以下才能查看

安装

```js
npm install webpack-dev-server -D
```

配置

```js
// package.json
"script":{
	"server":"webpack-dev-server"
}
```

webpack-dev-server在webpack.config.js中是可配置的

```js
devServer:{
	contentBase: path.resolve(__dirname,"./dist")
	open: true // 启动服务自动打开浏览器窗口
	port: 8080,
    before(app,server){ // mockserver,跨域解决方法之一
        app.get('/api/info', (req, res) => {
          res.json({
            hello: 'express'
          })
        })
    },
    proxy: { // 代理,解决跨域问题方法之一
        "/api": {
            target: "http://localhost:3000"
        }
    }
}
```

## mock

```shell
npm i express -D
npm i axios -D
```

```js
// server.js
const express = require('express');
const app = express();

app.get('/api/info', (req, res) => {
  res.json({
    hello: 'express'
  })
})

app.listen(3000)
```

```js
// 请求文件
import axios from 'axios'
axios.get('/api/info',(res)=>{
	console.log(res)
})
```

## Hot Module Replacement(HMR:热模块替换)

启动HMR

```js
const webpack = require('webpack')

devServer:{
	hot: true, // 热更新
	hotOnly: true // 即使HMR不生效,浏览器也不自动刷新
},
plugins: {
	new webpack.HotModuleReplacementPlugin()
}
```

处理js的HMR

```js
if(module.hot){ // 检测hmr的热更新是否开启
	module.hot.accept('./number.js',function(){//检测number.js的文件是否改变,改变执行回调
		/// 热更新操作
	})
}
// Vue和React中的vue-loader和react-hot-loader已经做好处理了
```

# babel

babel-loader是webpack和babel之间沟通的桥梁

@babel/core是babel语法的核心api库

@babel/preset-env是语法转换规则

@babel/polyfill是能转换promise等es6语法的

```shell
npm i babel-loader @babel/core @babel/preset-env @babel/polyfill -D
```

```js
{  
	test: /\.js$/,  
    exclude: /node_modules/,  
    use: {    loader: "babel-loader",    
        options: {      
            presets: [
                [
                    "@babel/preset-env",              
                    {                
                        targets: {                  
                            edge: "17",                  
                            firefox: "60",                  
                            chrome: "67",                  
                            safari: "11.1"                
                        },                
                        corejs: 2,//新版本需要指定核⼼心库版本 
                        useBuiltIns: "entry"//按需注⼊入 usage更好
                    } 
                ]
            ]    
        }  
    } 
}
```

