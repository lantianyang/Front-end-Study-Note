# webpack-cli

+ 安装
  ```shell
    npm install webpack -g
    npm install webpack-cli -g 
    ## 项目中安装
    npm install webpack-cli -D
  ```
# webpack打包

`webpack不安装插件或者Loader只能打包js和json文件，`

1. 运行命令
   
   + 开发环境： 
        ``` shell
            webpack ./src/index.js -o ./build/built.js --mode=development
        ```
        webpack会以./src/index.js为入口文件开始打包，打包后输出到./build/built.js
    + 生产环境
        ``` shell
            webpack ./src/index.js -o ./build/built.js --mode=production
        ```
`结论：生产环境和开发环境将es6模块化编译成浏览器能识别的模块化,生产环境比开发环境多出一个代码压缩过程`

2. 打包样式文件

    - webpack.config.js webpack的配置文件
    - 当运行webpack指令时，会加载里面的配置
    - 所有的构建工具都是基于nodejs平台运行，模块化默认采用commonjs

``` javascript
const { resolve } = require('path')
module.exports = {
    // webpack的入口
    entry: './src/index.js', // 入口文件
    // 输出
    output: {
        filename: 'built.js' ,// 输出文件名
        // __dirname nodejs的变量，代表当前文件目录的绝对路径
        path: resolve(__dirname,'build')
    },
    // loader配置
    module: {
        rules: [
            // 详细的loader配置
            {
                test: /\.css&/, // 匹配哪些文件
                // 使用哪些loader进行处理
                use: [
                    // use数组中loader执行顺序，数组顺序依次执行
                    'style-loader', // 创建style标签，将js中的样式资源插入进行，添加到head生效
                    'css-loader' // 将css文件变成commonjs模块加载js中，里面内容是样式字符串
                ]
            }
        ]
    },
    // plugins的配置
    plugins: [
        // 详细的plugins的配置
    ],
    // 模式
    mode : 'development' // 开发模式
    // mode : 'production' // 生产模式
}
```
    