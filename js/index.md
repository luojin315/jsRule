## 自定义全屏or缩小

``` javascript

var quite = document.getElementById('quite');
			quite.onclick = function() {
				exitFullScreen();
			}
			
function fullScreen(el) { //放大函数
				var rfs = el.requestFullScreen || el.webkitRequestFullScreen || el.mozRequestFullScreen || el.msRequestFullScreen,wscript;
console.log(el.webkitRequestFullScreen)
				if (typeof rfs != "undefined" && rfs) {
					rfs.call(el);
					console.log(el)
					return;
				}

				if (typeof window.ActiveXObject != "undefined") {
					wscript = new ActiveXObject("WScript.Shell");
					if (wscript) {
						wscript.SendKeys("{F11}");
					}
				}
			}

			function exitFullScreen(el) {//缩小函数
				var el = document,
					cfs = el.cancelFullScreen || el.webkitCancelFullScreen || el.mozCancelFullScreen || el.exitFullScreen,
					wscript;

				if (typeof cfs != "undefined" && cfs) {
					cfs.call(el);
					return;
				}

				if (typeof window.ActiveXObject != "undefined") {
					wscript = new ActiveXObject("WScript.Shell");
					if (wscript != null) {
						wscript.SendKeys("{F11}");
					}
				}
				}
```