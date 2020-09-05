# webpack安装

```shell
# 安装到最新的稳定版本
npm i -D webpack

# 安装指定版本
npm i -D webpack@<version>

# 安装到最新的体验版本,可能含有bug
npm i -D webpack@beta

# 安装webpack V4+版本时,需要额外安装webpack-cli
npm i -D webpack-cli

# 检查webpack版本
# npx是只想到node_modules/webpack/bin/webpack.js的软链接
npx webpack -v

# 启动webpack执行构建
npx webpack
```

# webpack构建

chunk是代码块,一个chunk可以使多个代码块组成的

bundle是资源文件

1Chunk = 1bundle

## webpack默认配置

- webpack默认支持JS模块和JSON模块
- 支持CommonJS、ES module、AMD等模块类型
- webpack4支持零配置使用,但是很弱,稍微复杂些的场景都需要额外扩展

**webpack运行`npx webpack`进行构建的时候,会去项目里找`webpack.config.js`,找到就按这个文件的配置来构建,没有这个文件就按照默认配置来构建**

```js
// 实现默认的webpack配置
const path = require('path');
module.exports = {
  // context: process.cwd(), 项目打包的相对路径,必须是绝对路径,默认是当前项目的根目录
  // entry入口支持字符串、数组、对象三种方式
  // entry: "./src/index.js", 执行构建的入口,默认是./src/index.js
  // entry: ['./src/index.js', './src/other.js'], 数组构建方式会把数组中的内容合并到构建的文件中
  entry: { // 对象的构建方式会根据键名打包到对应构建目录的对应文件中
    index: './src/index.js',
    other: './src/other.js'
  },
  output: { // 出口
    path: path.resolve(__dirname,"./dist"), // 构建的文件资源放在哪？必须是绝对路径
    filename: "main.js", // 构建的文件资源叫啥? 单入口的方式
    filename: "[name].js", // 多入口的方式,[]是占位符概念
  },
  mode: "development", // 构建模式,可选值:none,production,development
}
```

### 占位符

- hash:整个项目的hash,每构建一次,就会有一个新的hash值
- chunkhash:根据不同入口entry进行依赖解析,构建对应的chunk,生成相应的hash,只要组成entry的模块没有内容改动,则对应的hash不变
- name
- id

### 构建模式

- development
- production
- none

### loader

webpack默认只支持.json和.js模块,不支持其他格式的模块  

模块解析和模块转换器可用于把模块原内容按照需求转换成新内容,所以就需要loader来进行转换

loader的执行顺序是从后往前执行

### module

当webpack处理到不认识的模块时(除js和json),需要在webpack的module处进行配置,当检测到是什么格式的模块,就用什么loader来处理

```js
module:{  
	rules:[  
		{    
			test:/\.xxx$/,//指定匹配规则    
			use:{      
				loader: 'xxx-load'//指定使⽤用的loader    
			},
            // css-loader是把css模块内容加载到js模块中
        	// style-loader是在js中提取css内容,并在html中创建style标签,并将内容放入style标签中
            use: ['style-loader','css-loader']
		}  
	] 
}
```

### plugin

扩展插件，在 Webpack 构建流程中的特定时机注⼊入扩展逻辑来改 变构建结果或做你想要的事情。
作⽤用于整个构建过程

1. 下载插件
2. require引用插件
3. plugins:[new 插件构造函数]