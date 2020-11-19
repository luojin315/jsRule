## nodejs猜拳小游戏
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