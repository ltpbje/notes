# Node.js 入门

 JavaScript 运行时环境

定义:

![image-20230707111521355](./Typora-image/image-20230707111521355.png)

作用：使用 Node.js 编写服务器端程序

 ✓ 编写数据接口，提供网页资源浏览功能等等 

✓ `前端工程化`：为后续学习 Vue 和 React 等框架做铺垫 

## 什么是前端工程化？

前端工程化：开发项目直到上线，过程中集成的所有工具和技术 Node.js 是前端工程化的基础（因为 Node.js 可以主动读取前端代码内容）![image-20230707111806865](./Typora-image/image-20230707111806865.png)

## Node.js 为何能执行 JS？

首先：浏览器能执行 JS 代码，依靠的是内核中的 V8 引擎（C++ 程序）

 其次：Node.js 是基于 Chrome V8 引擎进行封装（运行环境） 

区别：都支持 ECMAScript 标准语法，Node.js 有独立的 API![image-20230707112317908](./Typora-image/image-20230707112317908.png)

==注意：Node.js 环境没有 DOM 和 BOM 等==

## Node.js的使用

### Node.js 安装

要求：下载 node-v16.19.0.msi 安装程序（指定版本：兼容 vue-admin-template 模板） 

安装过程：默认下一步即可 注释事项： 

1. 安装在非中文路径下

2.  无需勾选自动安装其他配套软件

成功验证： 

1. 打开 cmd 终端，输入 node -v 命令查看版本号 

2. 如果有显示，则代表安装成功

![image-20230707112513751](./Typora-image/image-20230707112513751.png)

### 使用 Node.js

需求：新建 JS 文件，并编写代码后，在 node 环境下执行 

命令：在 VSCode 集成终端中，输入 node xxx.js，回车即可执行![image-20230707112700420](./Typora-image/image-20230707112700420.png)

1. Node.js 是什么？ 
➢ 基于 Chrome 的 V8 引擎封装，独立执行 JavaScript 代码的环境 
2. Node.js 与浏览器环境的 JS 最大区别？ 
➢ Node.js 环境中没有 BOM 和 DOM
3. Node.js 有什么用？ 
➢ 编写后端程序：提供数据和网页资源等
➢ 前端工程化：集成各种开发中使用的工具和技术 
4. Node.js 如何执行代码？
➢ 在 VSCode 终端中输入：node xxx.js 回车即可执行（注意路径）

### fs 模块 - 读写文件

模块：类似插件，封装了方法/属性 

fs模块：封装了与本机文件系统进行交互的，方法/属性 

语法： 

1. 加载 fs 模块对象 
2. 写入文件内容 
3. 读取文件内容

### path 模块 - 路径处理

问题：Node.js 代码中，相对路径是根据终端所在路径来查找的，可能无法找到你想要的文件 p

建议：在 Node.js 代码中，使用==绝对路径== 

补充：`__dirname` 内置变量**（获取当前模块目录-绝对路径）** 

✓ windows： D:\备课代码\3-B站课程\03_Node.js与Webpack\03-code\03

 ✓ mac： /Users/xxx/Desktop/备课代码/3-B站课程/03_Node.js与Webpack/03-code/03 注意：path.join() 会使用特定于平台的分隔符，作为定界符，将所有给定的路径片段连接在一起

 语法：

1. 加载 path 模块 `const path require('path')`

2. 使用 path.join 方法，拼接路径`path.join('路径1'，'路径2'，..)`

## 案例

### 案例 - 压缩前端 html

需求：把 回车符（\r）和换行符（\n）去掉后，写入到新 html 文件中 

步骤： 

1. 读取源 html 文件内容 

2. 正则替换字符串 
3. 写入到新的 html 文件中

URL 中的端口号

 URL：统一资源定位符，简称网址，用于访问服务器里的资源 

端口号：标记服务器里不同功能的服务程序

端口号范围：0-65535 之间的任意整数 

![image-20230707223606990](./Typora-image/image-20230707223606990-1688740568272-1.png)

注意：http 协议，默认访问 80 端口 http://hmajax.itheima.net:80/api/province

## 常见的服务程序

 **Web 服务程序**：用于提供网上信息浏览功能 

注意：0-1023t 和一些特定端口号被占用，我们自己编写服务程序请避开使用

![image-20230708164730449](./Typora-image/image-20230708164730449.png)

1. 端口号的作用？

 ➢ 标记区分服务器里不同的服务程序 

2. 什么是 Web 服务程序？ 

➢ 提供网上信息浏览的程序代码

## http 模块-创建 Web 服务

需求：创建 Web 服务并响应内容给浏览器 

步骤：

1. 加载` http 模块`，创建 Web 服务对象 

2. 监听` request 请求事件`，设置响应头和响应体 3
3. 配置`端口号`并启动 Web 服务 

4. 浏览器请求 `http://localhost:3000 `测试 （localhost：固定代表本机的域名）
 ```js
   // 目标：基于http模块创建Web服务程序
   //1.4浏览器请求(http:/loca1host:3000)测试
  //1.1加载http模块，创建Web服务对象
   const http = require('http');
   const server = http.createServer();
   //1.2监听request请求事件，设置响应头和响应体
   server.on('request', (req, res) => {
       res.setHeader('Content-Type', 'text/plain;charset=utf-8');
       res.end('欢迎使用 Node.js 和 Http模块创建的Web服务');
   });
   //1.3配置端口号并启动Web服务
   server.listen(3000, () => {
       console.log('Web服务启动成功');
   });
 ```

   