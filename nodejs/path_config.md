## express设置静态文件路径
``` javascript
const path = require('path');
const express = require('express');
app.use(express.static(path.join(__dirname, 'static')));//static是相对于启动文件的静态文件路径
//js在项目中路径为 static/js/index.js  在页面中引入路径为 /js/index.js 前缀上一行已经是配置好了
```
## koa 设置静态文件路径
``` javascript
const path = require('path');
const Koa = require('koa');
app.use(static(path.join(__dirname + "/static/")))
```