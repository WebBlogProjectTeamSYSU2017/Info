# 项目文档

## 1. 测试运行结果

## 2. 项目资源来源



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

命令行输入如下指令进行安装：

```
>> go get github.com/WebBlogProjectTeamSYSU2017/backend
```

安装完成后输入如下指令运行：确保%GOPATH%/bin在系统环境变量内

```
>> backend.exe
```

## 5. 项目成员及成员小结
- [李志信](./李志信.md)
- [洪燊](./洪燊.md)
- [黄轲](./黄轲.md)
- [...]()
