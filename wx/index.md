## 微信小程序
- 文字超出两行显示...隐藏  
``` javascript
	display: -webkit-box;
	word-break: break-all;
	text-overflow: ellipsis;
	overflow: hidden;
	-webkit-box-orient: vertical;
	-webkit-line-clamp:2;/* 换行数 */
```

## CSS
- 可以达到边框虚线自定义长度效果
``` javascript
  background-image: linear-gradient(to bottom, red 0%, red 80%, transparent 50%);
  background-size: 3px 18px;
  background-repeat: y-repeat
```