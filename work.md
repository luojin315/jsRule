## 目前工作任务 看看A
1.开发问答小程序  （uniapp开发，最好使用HBuilder开发支持度很高）  
2.更新维护现有网站、页面（替换图片，更改文字链接）  
3.开发专题页面  
4.维护、开发360cube广告  
## 有用的文件线上地址
只关心按钮放大缩小动画效果js地址 ：[移动，pc都适配](https://cachejs.kuakao.com/kuakaoVip/2020922/11.11/js/wap.js)  

移动端易聊客服地址："https://cachejs.kuakao.com/kuakaoVip/2018jqr/swt-yd1.js"  

PC端易聊客服地址："https://cachejs.kuakao.com/kuakaoVip/2018jqr/swt-pcbj.js"  

公共js文件地址："https://cachejs.kuakao.com/public/js"  

rem文件地址："https://cachejs.kuakao.com/kuakaoWeb/wapkk/js/rem.js"

公共vue文件地址："https://cachejs.kuakao.com/public/js/vuejs/vue.js"

识别wap或pc端跳转功能js："https://cachejs.kuakao.com/kuakaoVip/2020922/11.11/js/common.js"（如果要考虑地址传参，可以在这之上更改，万人大联考js文件中有）

引用js文件地址前缀："https://cachejs.kuakao.com/"  
引用css文件、img文件地址前缀："https://cachecss.kuakao.com/"
## 本地文件地址
psd源文件存储位置：`E:\工作\psd `  
2020.8.10的开发任务存储位置：`E:\工作\2020.8.10jingpin`   
问答小程序位置：`E:\工作\2020.8.10jingpin\wenda`  
## 提交表单地址及约定
发送验证码地址(ajax为例)：  
```	
	url: 'https://wap.kuakao.com/sms/send',
	type: 'GET',
	async: false,
	dataType: "jsonp",  //指定服务器返回的数据类型
	data: {
		mobile:tel/*tel手机号，mobile形参名称不能改)*/ 
	},
```
验证 验证码地址(ajax为例)：  
```
	url: 'https://wap.kuakao.com/sms/validate',
	type: 'GET',
	async: false,
	dataType: "jsonp",  //指定服务器返回的数据类型
	data: {
		code: formVal.yzm /*yzm验证码，code形参名称不能改*/ 
	},
	
	if (data.status == '1') {/*返回"1"为验证码正确*/ 
		
	}
	
```
提交表单地址  
```
 $.ajax({
	url: 'https://wap.kuakao.com/formguide/index?fid=121',/*提交表单地址，应该只会改fid=数字)*/
	type: 'post',
	async: false,
	data: {
		name: "姓名[|]"+formVal.name,/*每个实参前需要加上对这个参数的描述"~~[|]",约定不可更改*/ 
		tel: "手机号[|]"+formVal.phone,/*传手机号的形参tel不可更改，其他的没规定*/ 
		diqu: "所在地区[|]"+formVal.city,
		add: "页面链接[|]"+formVal.href,/*每个提交的表单需要加上页面链接，策划那边会统计*/ 
	},
	success: function (res) {
		if (res == 1 || res == true) {/*成功提交传回的值 1||true*/ 
			alert('提交成功');
		   
		}
		$(list.el)[0].reset();//提交表单后清除表单内容，提交表单后清除表单中数据
	},

})
```

## 360cube基本配置
360cube：  
[360cube开发文档地址](https://cube.360.com/docs)  
运行项目使用命令行进入cubetest文件夹
运行输入`cubetool run`在浏览器访问：http://localhost:3600 即可访问。应该会自动打开  
上传cube需要先验证token，token在360cub平台中账号设置里  
上传前准备：
1.输入`cubetool login`把复制好的token粘贴ok  
2.检查cube.json文件中cubeID是否对应
```
{
	"id": "QebNNoQcokN",//cubeID
	"version": "1.0.0",//版本号
	"name": "21考研大纲",//左上角的cube名称
	"ie": 9,
	"miniapp_only": false,
	"disable_expand": false,
	"launchimg": "assets/launchimg.png",
	"files": [//需要上传的文件
		"cube.tpl",
		"cube.css",
		"cube.js",
		"assets/launchimg.png"
	]
}
```
准备好，输入`cubetool publish` 上传成功，到对应的cube中提交审核

