# vue

## 一：webpack配置文件(webpack.config.js)

### 1.npm run dev运行压缩文件

（1）devlopment生成时速度快，但是文件较大，适合开发时使用

（2）product模式生成时速度慢，但是压缩文件更小，适合开发结束，项目上线的时候使用

### 2.webpack.config基础使用

```js
module.exports = {

  mode: 'development',

  //mode用来指定构建模式，可选值又development和production

  entry: Path.join(__dirname, './src/index.js'),

  // entry用来指定打包入口文件目录

  output: {

​    path: path.join(__dirname, 'dist'),

​    filename: 'bund.js'

  },

  // 指定要压缩生成的文件存放路径以及存放文件的名称

}
```

### 3.webpack中的插件

```js
npm i webpack-dev-sever@3.11.2 -D     
//可以类似于node中的nodemon一样，自动保存更新
//当修改了源码，webpack回自动进行项目的打包和构建
npm i html-webpack-plugin@5.3.2 -D
自动进入dev研发阶段的项目页面（类似于一个模板引擎插件）
const HtmlPlugin = require('html-webpack-plugiin')
const htmlPlugin = new HtmlPlugin({
template: './scr/index.html',
    filename: './index.html',
})

modul.exports = {
    mode: 'devlopment',
    plugins: [htmlPlugin],
}
```

###  4.loader

在实际开发过程中，webpack默认只能打包处理以.js为后缀的模块，其他非.js后缀名的魔魁啊。默认处理不了，需要调用loader加载器才可以正常打包，否则回报错。

#### 1.加载器的作用

css-loader可以打包i处理.css的文件

less-loader可以打包处理.less的文件

babel-loader可以打包处理webpack无法处理的高级js语法

####  2.打包处理css文件

```
//运行npm i style-loader@3.0.0 css-loader@5.2.6 -D 命令，安装处理css文件的loader
//在webpack.config.js的 module->rules数组中，添加loader规则如下
module: {
rules: [//文件后缀名的匹配规则]
//对应了不同模块对应的loader
	{
	test: /\.css/, usse: ['style-loader', 'css-loader']
	}
}
//其中，test表示匹配的文件类型， use表示对应要调用的loader
```

![image-20230123162445655](C:\Users\26424\AppData\Roaming\Typora\typora-user-images\image-20230123162445655.png)

####  3.打包处理less文件

```
运行 npm i less-loader@10.0.1 less@4.1.1 -D
在webpack.config.js ->rules数组中，添加loader规则如下
module: {
rules: [
{
test: /\.less$/, use: ['style-loader', 'css-loader','less-loader']
}
]
}
```

#### 4.打包处理图片

![image-20230123165948710](C:\Users\26424\AppData\Roaming\Typora\typora-user-images\image-20230123165948710.png)

#### 5.当遇到高级js语法，而且webpack辨识不了时需要安装babel-loader包

![image-20230126114503355](C:\Users\26424\AppData\Roaming\Typora\typora-user-images\image-20230126114503355.png)

![image-20230126114952886](C:\Users\26424\AppData\Roaming\Typora\typora-user-images\image-20230126114952886.png)

### 5.打包发布

#### 1.生成js目录

![](C:\Users\26424\AppData\Roaming\Typora\typora-user-images\image-20230126120757028.png)

#### 2.生成image目录![image-20230126120956257](C:\Users\26424\AppData\Roaming\Typora\typora-user-images\image-20230126120956257.png)

#### 3.自动删除dise目录![image-20230126121504456](C:\Users\26424\AppData\Roaming\Typora\typora-user-images\image-20230126121504456.png)

#### 4.更新检查报错

#### ![image-20230126135524671](C:\Users\26424\AppData\Roaming\Typora\typora-user-images\image-20230126135524671.png)(C:\Users\26424\AppData\Roaming\Typora\typora-user-images\image-20230126135408189.png)