## node教程:
http://javascript.ruanyifeng.com/nodejs/http.html
https://www.w3cschool.cn/nodejs/2vgu1pwn.html

## 模块的分类:
> 1.核心模块
``` bash
http     fs     path
var http=require('http');	
var fs=require('fs');	 //读取文件
```
> 2.文件模块
``` bash
var math=require('./a.js');
```
> 3.第三方模块
``` bash
var async=require('async');
```
## console(控制台对象):
``` bash
1.标准输出流
console.log()
2.返回信息性消息
console.info()
3.输出红色错误信息
console.error()
4.输入警告
console.warn()
5.输出时间,表示计时开始结束
console.time(label)
console.timeEnd(label)
```
## fs(文件模块):
``` bash
readFileSync方法用于同步读取文件并返回一个字符串:
var text=fs.readFileSync(fileName,"utf8");
readFile方法用于异步读取文件:
fs.readFile(fileName,"utf8",function(err,text){});

读取文件:
fs.readFile(文件名,function(error,data){})
写文件:
fs.writeFile(文件名,内容,function(error){})
重命名:
fs.rename(原始文件,新文件,(err)=>{
console.log(err);
})
```

## querystring(处理query字符串模块):
``` bash
var GET={};
var querystring=require('querystring');
if(req.url.indexOf('?')!=-1){
var arr=req.url.split('?');
var url=arr[0];
GET=querystring.parse(arr[1]);
}else{
var url=req.url;
}
console.log(url,GET);
```

## URL(解析url模块):
``` bash
const urlLib=require('url');

var obj=urlLib.parse(req.url,true);	//true 解析query成json

var url=obj.pathname;	//pathname 地址
var GET=obj.query;		//query 数据(参数)
console.log(url,GET);
```

## 接收post数据:
``` bash
POST数据很大--分段传输
data  一段数据到达
end 	 全部到达

const querystring=require('querystring');
var str='';
req.on('data',function(data){
str+=data;
});
req.on('end',function(){
console.log(str);
var POSTquerystring.parse(str);
console.log(POST)
})
```

## 发送给用户错误的信息:
``` bash
res.status(500).send('错误').end();
```

## 跨域设置请求头:
``` bash
server.use('/login',(req,res)=>{
  res.setHeader('Access-Control-Allow-Origin','*');
})
```


## Crypto(加密-模块):
> 安装:
``` bash
  cnpm i crypto
```
> 应用:
``` bash
const crypto=require('crypto');

var obj=crypto.createHash('md5');
obj.updata('123456');
var str=obj.digest('hex');
console.log(str)
```
> 模块:
``` bash
const crypto=require('crypto');

module.exports={
MD5_SUFFIX:'lang_strive@163.com',
md5:function(str){  //传需要加密的文件
var obj=crypto.createHash('md5');
obj.updata('123456');
return obj.digest('hex');
}
}
```
> 校验:
``` bash
const common=require('./libs/common.js');

var str='123456';
var str2=common.md5(str+common.MD5_SUFFIX);
```


## Events(事件-模块):

## Net(网络操作-模块):

## OS(操作系统信息-模块):

## Path(处理文件路径-模块):
``` bash
var obj=path.parse('c:\\web\\node\\a.html');
//base          文件名部分
//ext		扩展名
//dir		路径
//name	        文件主体部分
console.log(obj);
```

## Stream(流操作-模块):

## Timers(定时器-模块):

## ZLIB(压缩-模块):
