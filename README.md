webpack介绍
https://www.jianshu.com/p/42e11515c10f
1.是个啥？怎么工作的？
2.准备
  1.新建一个文件夹demo
  2.在demo中创建一个package.json文件   npm init 一路回车
  3.创建文件夹
    ./public index.html 
    ./app  Greeter.js  main.js
    #index.html写最基础的html代码，然后引入打包后的js文件（经过webpack打包后命名为bundle.js）
    #Greeter.js 定义一个函数，并将该函数导出为一个模块
    #main.js引入该模块
3.使用webpack
  1.终端使用
  2.通过配置文件使用webpack
    1.新建配置文件webpack.config.js
        module.exports = {
          entry:  __dirname + "/app/main.js",   //唯一入口文件,“__dirname”是node.js中的一个全局变量，它指向当前执行脚本所在的目录
          output: {
            path: __dirname + "/public",        //打包后的文件存放的地方
            filename: "bundle.js"               //打包后输出文件的文件名
          }
        }
        
       这样的话，终端只需要运行：webpack即可
    2.连webpack命令都不需要，修改package.json文件配置scripts对象
        {
          "name": "webpack-sample-project",
          "version": "1.0.0",
          "description": "Sample webpack project",
          "scripts": {
            "start": "webpack" // 修改的是这里，JSON文件不支持注释，引用时请清除
          },
          "author": "zhang",
          "license": "ISC",
          "devDependencies": {
            "webpack": "3.10.0"
          }
        }
        
        这时只需要npm start就可以了
    3.webpack的强大功能：
        1.生成source maps,对应编译文件和源文件,方便查错调试
          在webpack的配置文件中配置dev-tool
        2.使用webpack构建本地服务器
          配置devserver，修改package.json中script对象
        3.loader能够对不同格式文件处理：把下一代js文件转换为浏览器兼容的js文件
          配置module
        4.babel 一个javascript编译平台
          1.工作
            使用最新的js代码
            使用扩展语法
          2.是由几个核心包组成，按需安装使用
          3.配置，webpack.config.js中的module,内容多的话就单独一个配置文件.babelrc
        5.安装react
          1.修改Greeter.js文件，返回一个react组件
          2.修改main.js文件，也是ES6语法
          3.重新npm start
        6.一切皆模块css
          1.webpack提供两个工具样式表
            1.css-loader 使能@import和url(...)实现require
            2.style-loader 将所有计算后的样式加入到页面中
            3.两者组合能够把样式表嵌入webpack打包后的js文件中
            4.配置 module(loaders)
          2.css modules
            可以直接把CSS的类名传递到组件的代码中，这样做有效避免了全局污染。
             配置css-loader
          3.css预处理器
        7.插件配置
        8.优化
          1.压缩
          2.缓存
          3.去无关
          
          
        
        
          
    
    
