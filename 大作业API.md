# API文档

## Overview

Ⅰ.  [Schema](#schema)

Ⅱ. [Authentication & Client Errors](#authentication)

Ⅲ. [HTTP Verbs](#http)

Ⅳ. [APIs](#apis)



## <span id="schema">Schema</span>

所有的API都通过HTTPS访问，所有数据都以`JSON`的格式传输。默认通过通过本地ip地址`127.0.0.1`访问，端口为`8080`，可在文件config/index.js中修改连接API的根url，例：

```
    // Paths
    assetsSubDirectory: 'static',
    assetsPublicPath: '/',
    proxyTable: {
      '/api': {
        target: 'http://localhost:8082', //可修改为其他端口或ip地址
        changeOrigin: true,
        ws: true,
        pathRewrite: {
          '^/api': ''
        }
      }
    },
```



## <span id="authentication">Authentication & Client Errors</span>

用户登录请求可以使用header中的token或者body中的账户信息进行验证。

除了用户创建和用户登录请求外，其他所有请求都通过验证token是否有效来判断请求是否有效，假如token有效，则返回请求的相关资源；假如token无效，则返回相应的错误提示。

返回的HTTP状态码都为200，将错误信息保存在返回的`JSON`文件中，所有API的请求都返回以下结构的`JSON`文件：

```
{
	"ok" : bool
	"data" :  string/json
}
```

其中`ok`字段表示本次请求是否成功，成功时为`true`，失败时为`false`。假如请求成功，`data`字段为相应的资源，为`JSON`格式；假如请求失败，则`data`字段为错误信息，为`string`格式。



## <span id="http">HTTP Verbs</span>

| Verb   | Description                                        |
| ------ | -------------------------------------------------- |
| GET    | 用于检索资源（博客）                               |
| POST   | 用于新建资源（博客、用户），或执行用户动作（登录） |
| DELETE | 用于删除资源（博客）                               |



## <span id="apis">APIs</span>

### 用户创建 [url: /signup]

```
method:POST
body:
{
	"username":"username"
	"email": "382673304@qq.com"
	"password":"123456"
}
```
返回值：
```
{
	"ok" : bool: 是否创建成功
	"data" :  string：错误信息
}
```

### 用户登录 [url: /login]
```
method:POST
head:{
	"token":"XXXXX" //可以为空
}
body:
{
	"email": "382673304@qq.com"
	"password":"123456"
}
```
返回值:
```
{
	"ok" : bool: 是否登录成功
	"data" :  string：错误信息
}
```

### 博客创建 [url: /{email}/createblog/]
```
method:POST
head:{
	"token":"XXXXX" //可以为空
}
body:
{
	"title": string 博客标题
	"ispublic": string 是否公开："0" 为私密
	"content": string博客内容
	"tag": string 博客摘要
}
```
返回值:
```
{
	"ok" : bool: 是否创建成功
	"data" :  string：错误信息
}
```

### 获取当前用户所有博客 [url: /{email}/bloghome/]
```
method:GET
head:{
	"token":"XXXXX" 
}
body:
{
	
}
```
返回值:
```
{
	"ok" : bool: 是否获取成功
	"data" :{
		{"id":"dagwewewfcwfedcwe",
		"creatoremail":"1111@qq.com"
		,"createtime":"2019-11-28 23:25:48",
		"title":"你好呀_private",
		"ispublic":"0",
		"content":"hellow world",
		"tag":"这是tag"},
		
		{"id":"dagwewewfcwfedcwe",
		"creatoremail":"1111@qq.com"
		,"createtime":"2019-11-28 23:25:48",
		"title":"你好呀_private",
		"ispublic":"0",
		"content":"hellow world",
		"tag":"这是tag"},
		...
	}
}
```

### 获取所有可见博客 [url: /{email}/blogground/]
```
method:GET
head:{
	"token":"XXXXX" 
}
body:
{
	
}
```
返回值:
```
{
	"ok" : bool: 是否获取成功
	"data" :{
		{"id":"dagwewewfcwfedcwe",
		"creatorname":"LZX"
		,"createtime":"2019-11-28 23:25:48",
		"title":"你好呀_private",
		"content":"hellow world",
		"tag":"这是tag"},
		
		{"id":"dagwewewfcwfedcwe",
		"creatorname":"LZX"
		,"createtime":"2019-11-28 23:25:48",
		"title":"你好呀_private",
		"content":"hellow world",
		"tag":"这是tag"},
		...
	}
}
```

### 删除自己的博客 [url: /{email}/bloghome]
```
method:DELETE
head:{
	"token":"XXXXX" 
}
body:
{
	"id": "dwogejge"string 博客ID
}
```
返回值:
```
{
	"ok" : bool: 是否获取成功
	"data" : string 错误信息
}
```
