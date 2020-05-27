# Hello World

`js文件`
``` javascript
console.log('Hello World')
```
`命令行执行js文件`
``` shell script
node helloworld.js
```
# 读写文件

## 读取文件

``` javascript
// fs是file-system的简写，就是文件系统的意思
// 在Node中如果想要进行文件操作，就必须引入fs这个核心模块
// 在fs这个核心模块中提供了文件操作相关的API

// 使用require方法加载fs核心模块
var fs = require('fs')

// 读取文件
// 第一个参数为读取文件的路径，第二参数是回调函数，
// error 如果读取失败，error是错误对象，读取成功error就是null
// data  如果读取失败，data为null，读取成功data是文件数据
fs.readFile('./hello.json', (error, data) => {
    // 文件内是二进制数据，直接输出data为16进制，需要toString()才能看到可读的数据
    if (!error) {
        console.log(data.toString())
    } else {
        console.error(error)
    }
})
```

## 写入文件
``` javascript
var fs = require('fs')

// 参数一 要写入文件的路径
// 参数二 要写入的内容
// 参数三 写入的回调函数
let params = {
    name: "蓝天阳"
}
fs.writeFile('./hello.json', JSON.stringify(params), (error) => {
    // 写入成功error为null 写入失败error为错误对象
    if (!error) {
        // ... 
    }
})
```

# http服务

``` javascript
var http = require('http');
var server = http.createServer();
server.on('request', () => {
    console.log('hello world')
})
server.listen(3081, () => {
    console.log('服务器启动成功！')
})

var http = require('http');
var server = http.createServer();
// request 请求事件处理函数，需要接受两个函数
// request 请求对象 获取客户端的请求信息 请求头等，请求参数。。。
// response 响应参数 用来给客户端发送消息
server.on('request', (request, response) => {
    // write可以多次使用，但是一直到end才会结束，否则客户端就会一直处于等待状态
    response.write('hello')
    response.end()
})
server.listen(3081, () => {
    console.log('服务器启动成功！')
})
```