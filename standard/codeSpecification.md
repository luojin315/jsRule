# 代码规范
## 命名
- 采用小写驼峰命名 lowerCameCase（首字母小写），代码命名均不能以下划线开头，也不能以下划线或美元符号结尾  
bad:
``` javascript
    _name   name_   name$
```
- 方法名、参数名、成员属性（对象属性）、局部变量均使用小写驼峰命名  
``` javascript
    getValue  setValue
```
- 构造器函数使用首字母大写  
``` javascript
    Animal
```
- 方法名必须是动词或者**动词+名词**形式
- **增加、删除、获取、更改统一使用动词：**
``` javascript
    add/增加    delete/删除    get/获取    updata/更改
    例（更改dom元素函数名）：updataBox
```
- 函数常用方法动词：
``` javascript
get 获取       /       set 设置
add 增加       /       remove 删除
create 创建    /       destory 移除
start 启动     /       stop 停止
open 打开      /       close 关闭
read 读取      /       write写入
load 载入      /       save 保存
begin 开始     /       end 结束
backup 备份    /       restore 恢复
import 导入    /       export 导出
split 分割     /       merge 合并
inject 注入    /       extract 提取
```
## js代码格式
- js代码字符串统一使用单引号'string',需要转义的的地方除外
- 长命名与运算符空格分组
``` javascript
   bad: Thisisavarofthings=yourfuckingtype+otherdamnedresult*me;
   good: oh = mygodblessedsweetheart - thesaintangel / cursedcorpsehere;
```
- 函数使用声明函数方式，而不是函数表达式
``` juavascript
good：
    function f () {
        
    }
bad:
    var f = function () {
        
    }
```
- 创建对象、数组
``` juavascript
例：
    const a={};
    const b=[];
    成员属性在括号中声明 const a={
        name:"张三"
    }
```
- 使用对象方法简写方式
``` juavascript
good：
    const a = {
        name:"张三",
        fun() {
            console.log(a.name);
        }
    }
bad:
    const a = {
        name: "张三",
        fun: function() {
            console.log(a.name);
        }
    }
```
- 逗号后接空格
``` javascript
例：
    var a = 1, b = 2;
    ary = [1, 2, 3, 4]
```
- 对象字面量键和值不能存在空格，且要求对象字面量的冒号和值之间存在一个空格
``` javascript
bad：
    var obj = { 'name' : "zhangsan" };
good:
    var obj = { 'name': "zhangsan" };
```
- 代码块前加空格
``` javascript
bad：
    function f(){
        
    }
good:
    function f() {
        
    }
```
## 引入文件规范
- style文件在head标签中引入
- js文件在body尾部引入(如需页面加载完成前判断用户端类型可加在head标签中)