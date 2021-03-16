## 连续结构赋值并且更改解构出来的值命名
```
let obj={a:{b:{c:1}}}
const {a:{b:{c:data}}} = obj
这样解构赋值并且将c更改变量名为data
```