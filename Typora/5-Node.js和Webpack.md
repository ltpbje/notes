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

## Node.js 安装

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