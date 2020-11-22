## nodejs猜拳小游戏
``` javascript
<!-- 引入 -->
module.exports = function (user) {
		var random = Math.random() * 3;

		var computerActive = "";

		if (random < 1) {
			computerActive = "rock"
		} else if (random > 2) {
			computerActive = "cloth"
		} else {
			computerActive = "scissor"
		}

		console.log(computerActive);

		if (user == computerActive) {
			console.log("平局");
			return 0;
		} else if (
			(computerActive == "rock" && user == "cloth") ||
			(computerActive == "cloth" && user == "scissor") ||
			(computerActive == "scissor" && user == "rock")
		) {
			console.log("玩家赢");
			return -1;
		} else {
			console.log("电脑赢");
			return +1;
		}
}

<!-- main.js -->
 var common = require('../common.js');


var user = process.argv[process.argv.length - 1];

var num = 0;

process.stdin.on('data', e => {
    const user = e.toString().trim();

    const result = common(user);
    if(result == -1) {
        num++;
    }
    if(num == 3) {
        console.log("你赢了");
        process.exit();
    }
    console.log(num)
})
```
## 事件发射器events
``` javascript
const Event = require('events').EventEmitter;
class Time extends Event{
	constructor() {
		super();
		setInterval(() => {
			this.emit('new', {
				price: Math.random() * 100
			})
		},1000);
	}
}
const time = new Time;
time.addListener('new', (res) => {
	if(res.price < 80){
		console.log("buy!")
	}
})


```

## nodejs同步异步消耗时间对比（npm install glob）
``` javascript
const glob = require('glob')

let result = null;
//异步：
console.time("f")
glob(__dirname + '/**/*', function(err, res) {
	result = res;
});
console.timeEnd("f")
//同步：
console.time("s");
result = glob.sync(__dirname + '/**/*')
console.timeEnd("s")
```
## express设置接口跨域
``` javascript
app.all("*", function (req, res, next) {
	//设置允许跨域的域名，*代表允许任意域名跨域
	res.header("Access-Control-Allow-Origin", req.headers.origin || '*');
	// //允许的header类型
	res.header("Access-Control-Allow-Headers", "Content-Type, Authorization, X-Requested-With");
	// //跨域允许的请求方式 
	res.header("Access-Control-Allow-Methods", "PUT,POST,GET,DELETE,OPTIONS");
	// 可以带cookies
	res.header("Access-Control-Allow-Credentials", true);
	if (req.method == 'OPTIONS') {
		res.sendStatus(200);
	} else {
		next();
	}
})
```