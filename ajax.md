Ajax

> 异步:在等待响应的过程中，不会阻塞在当前页面，浏览器可以做自己的事情，直至成功获取响应后，浏览器才开始处理响应数据

> XML是前后端信息传输数据的一种格式

Ajax是服务器与浏览器之间的一种异步通信方式

Ajax 可以不全部重新加载页面，而加载某个部分

#### 基本用法

```html
    // Ajax  想要实现浏览器与服务器之间的异步通信，需要依靠XMLHttpRequest 它是一个构造函数
    // 使用步骤
    // 1.创建xhr对象
    const xhr = new XMLHttpRequest;
    // 2.准备发送请求
    xhr.open{'HTTP,通过请求体携带数据方法POST,GET ,PUT DELETE'}
    // 3.发送请求
    xhr.send(null);

    // 4.监听事件 处理响应
    // 当获取响应后，会触发xhr对像的readystatechange事件对响应事件进行处理
    xhr.onreadystatechange = ()=>{
        if(xhr.readyState !==4)return;
        if ((xhr.status >= 200)&(xhr.status < 300)||xhr.status === 304){
        console.log(xhr.responseText) // 正常响应数据
        }
    };
    // 0:未初始化  党委调用open()
    // 1:启动 已经调用open(),但尚未调用send
    // 2:发送 调用send(),但未接收到响应
    // 3:接收 已经受到部分响应
    // 4.完成 收到全部响应
```



##### GET请求

不能通过请求体携带数据，但可以通过请求头部携带

> const url = '连接+?明值对&明值对&明值对'  （明值对 有限制）

##### POST请求

主要通过请求体携带数据，也可以通过请求头携带

> 传输数据可以使用send()  // 一般参数位置是字符串
>
> xhr .send(`key=value&key=value`)  