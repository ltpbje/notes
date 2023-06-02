

# 1.AJAX 

## 1.1 AJAX 简介

简介 AJAX 全称为 Asynchronous JavaScript And XML，就是==异步的 JS 和XML==。通过 AJAX 可以在浏览器中向服务器发送异步请求，最大的优势：==无刷新==获取数据。AJAX 不是新的编程语言，而是一种将现有的标准组合在一起使用的新方式。

## 1.2 XML简介

XML 简介 XML 可扩展标记语言。 XML 被设计用来传输和存储数据。 XML 和 HTML 类似，不同的是 HTML 中都是预定义标签，而 XML 中没有预定义标签，全都是自定义标签，用来表示一些数据。

```
比如说我有一个学生数据：
name = "孙悟空" ; age = 18 ; gender = "男" ;
用 XML 表示：
    <student>
    <name>孙悟空</name>
    <age>18</age>
    <gender>男</gender>
    </student>
```

现在已经被 JSON 取代了。

```
用 JSON 表示：
	{"name":"孙悟空","age":18,"gender":"男"}
```

## 1.3 AJAX 的特点 

### 1.3.1 AJAX 的优点 

可以无需刷新页面而与服务器端进行通信。 

允许你根据用户事件来更新部分页面内容。

### 1.3.2 AJAX 的缺点 

1.没有浏览历史，不能回退 

2.存在跨域问题(同源) 

3.SEO 不友好

## 1.4 AJAX 的使用

###  1.4.1 核心对象 XMLHttpRequest

AJAX 的所有操作都是通过该对象进行的。

### 1.4.2 使用步骤

```
//获取button元素
        const btn = document.getElementsByTagName('button')[0];
        const result = document.getElementById("result");
        //绑定事件
        btn.onclick = function(){
            //1. 创建对象
            const xhr = new XMLHttpRequest();
            //2. 初始化 设置请求方法和 url
            xhr.open('GET', 'http://127.0.0.1:8000/server?a=100&b=200&c=300');
            //3. 发送
            xhr.send();
            //4. 事件绑定 处理服务端返回的结果
            // on  when 当....时候
            // readystate 是 xhr 对象中的属性, 表示状态 0 1 2 3 4
            // change  改变
            xhr.onreadystatechange = function(){
                //判断 (服务端返回了所有的结果)
                if(xhr.readyState === 4){
                    //判断响应状态码 200  404  403 401 500
                    // 2xx 成功
                    if(xhr.status >= 200 && xhr.status < 300){
                        //处理结果  行 头 空行 体
                        //响应 
                        // console.log(xhr.status);//状态码
                        // console.log(xhr.statusText);//状态字符串
                        // console.log(xhr.getAllResponseHeaders());//所有响应头
                        // console.log(xhr.response);//响应体
                        //设置 result 的文本
                        result.innerHTML = xhr.response;
                    }else{

                    }
                }
            }


        }
```

1) 创建 XMLHttpRequest 对象 var xhr = new XMLHttpRequest();

2) 设置请求信息 xhr.open(method, url);//可以设置请求头，一般不设置
3) 发送请求 xhr.send(body) //get 请求不传 body 参数，只有 post 请求使用
4) 接收响应 //xhr.responseXML 接收 xml 格式的响应数据 //xhr.responseText 接收文本格式的响应数据

```
 xhr.onreadystatechange = function () {
                if (xhr.readyState === 4) {
                    if (xhr.status >= 200 && xhr.status < 300) {
                        // 处理服务端返回的结果
                        result.innerHTML = xhr.response;
                    }
                }
```

