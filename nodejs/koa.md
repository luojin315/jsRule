## koa-mount路由
``` javascript
需要注意的是ko-mount的路由 / 代表通配符，只要把这个路由放第一个会直接进入这个中间件，一般
/ 作为匹配404页面
```
## koa改造后的猜拳游戏 利用了await 抽取逻辑层
``` javascript
var playerWinCount = 0;
app.use(
	mount('/game', gameLogic)
)

gameLogic.use(
	async function (ctx, next) {
		console.log(playerWinCount)
		if (playerWinCount >= 3) {
			ctx.status = 200;
			ctx.body = {
				code: 500,
				message: "不玩了",
				data: {
					user: "luojin"
				}
			}
			return ;
		}
		await next();
		if (ctx.play) {
			playerWinCount++;
		}
	}
)

gameLogic.use(
	async function (ctx) {
		const query = ctx.query;
		const userActive = query.userActive;
		var random = Math.random() * 3;
		var computerActive = "";

		if (random < 1) {
			computerActive = "rock"
		} else if (random > 2) {
			computerActive = "cloth"
		} else {
			computerActive = "scissor"
		}
		ctx.status = 200;
		if (userActive == computerActive) {
			ctx.body = {
				code: 200,
				message: "平局",
				data: {
					user: "luojin"
				}
			}
			return 0;
		} else if (
			(computerActive == "rock" && userActive == "cloth") ||
			(computerActive == "cloth" && userActive == "scissor") ||
			(computerActive == "scissor" && userActive == "rock")
		) {
			ctx.body = {
				code: 200,
				message: "你赢了",
				data: {
					user: "luojin"
				}
			}
			ctx.play = true;
			return +1;
			
		} else {
			ctx.body = {
				code: 200,
				message: "你输了",
				data: {
					user: "luojin"
				}
			}
			return -1;
		}
	}
)
```