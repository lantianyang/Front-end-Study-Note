# 安装依赖和构建项目

``` shell script
## 全局安装typescript
npm install -g typescript
## 构建nodejs项目
npm init
## 生成tsconfig文件
tsc --init
## 安装koa依赖
npm i koa koa-router typescript ts-node nodemon @types/koa @types/koa-router @types/node typescript -D
```
## 修改package.json

``` javascript
"scripts": {
    "test": "echo \"Error: no test specified\" && exit 1",
    "start": "tsc && node app.js"
}
```
# 运行项目
- app.ts代码
``` typescript 
const Koa = require('koa');
const app = new Koa();
 
app.use(async ctx : any => {
    ctx.body = 'Hello World';
});
app.listen(3000);
```
- 启动项目

``` shell script
npm run start
```