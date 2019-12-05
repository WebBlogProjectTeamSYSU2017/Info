# 项目文档

## 1. 测试运行结果

#### 登录界面

注册后输入相应账户密码即可登录成功。

![0.PNG](https://github.com/WebBlogProjectTeamSYSU2017/Info/blob/master/pics/0.PNG?raw=true)

#### 写博客

输入相应内容，点击上传

![1.png](https://github.com/WebBlogProjectTeamSYSU2017/Info/blob/master/pics/1.png?raw=true)

#### 我的博客

发布成功后，在“我的博客”一栏可以看到已发布博客。显示的摘要部分即写博客时填写的“博客概述”。

![2.PNG](https://github.com/WebBlogProjectTeamSYSU2017/Info/blob/master/pics/2.PNG?raw=true)

#### 博客广场

在“博客广场”一栏，可以看到所有账户发布的所有公开博客。显示了博客的摘要、作者、发布时间。

![5.PNG](https://github.com/WebBlogProjectTeamSYSU2017/Info/blob/master/pics/5.PNG?raw=true)

#### 阅读

点击“阅读”按钮，跳出阅读框，显示博客的全部内容

![6.PNG](https://github.com/WebBlogProjectTeamSYSU2017/Info/blob/master/pics/6.PNG?raw=true)



## 2. 项目资源来源

以上作为测试例子的博客来源于 [CSDN博客1](https://blog.csdn.net/u014427391/article/details/102785219)、[CSDN博客2](https://blog.csdn.net/csdnnews/article/details/103097703)



## [3. 项目API](./大作业API.md)



## 4. 安装指南

### 4.1 前端安装指南

将项目clone到本地后，使用指令安装依赖
```
npm install
```
依赖安装完成后使用指令运行前端于localhost:8080
```
npm run dev
```
**可在**文件config/index.js中修改前端运行url位置，例：

```
host: '172.19.13.200', // can be overwritten by process.env.HOST
port: 8080, // can be overwritten by process.env.PORT, if port is in use, a free one will be determined
```
**可在**文件config/index.js中修改连接的后端根url，例：
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

### 4.2 后端安装指南

命令行输入如下指令进行安装（需要事先安装`go mod`）：

```
>> go get github.com/WebBlogProjectTeamSYSU2017/backend
```

安装完成后输入如下指令运行：确保%GOPATH%/bin在系统环境变量内

```
>> backend.exe
```

也可以在go工作空间下手动`go install`获得可执行文件

## 5. 项目成员及成员小结
- [李志信](./李志信.md)
- [洪燊](./洪燊.md)
- [黄轲](./黄轲.md)
- [赖俞静](./赖俞静.md)
- [...]()
