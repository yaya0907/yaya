### 跨域

> 不同域之间的请求，就是跨域请求

> // 同域
>
> const url = './index.html'
>
> const xhr = new XMLHttpRequst();
>
> xhr.onreadystatechange=()=>{
>
> xhr.open('GET',url,true);
>
> xhr.send(null); 
>
> }

https(协议)://www.*****.com(域名):123(端口号)/course/list(路径)

其中除路径外任何一个不同都不同域

组织跨域请求是==浏览器==本身的一种安全策略-同源策略

客户端或服务器不存在跨域被阻止问题

#### 解决方案

##### CORS跨域资源共享

> Access-Control-Allow-Origin:*
>
> // 表明语序所有域名来跨域请求它,*是通配符没有任何限制
>
> Access-Control-Allow-Origin:cbunoqscvjuis 指定域请求

> 跨域过程
>
> 1.浏览器发送请求
>
> 2.都断在响应头中添加Access-Control-Allow-Origin头信息
>
> 3.浏览器接受到响应
>
> 4.同域下的请求，浏览器不会额外做什么，前后端通信圆满完成
>
> 5.跨域请求，通信圆满完成
>
> 6.找不到就丢弃响应结果

> 兼容性
>
> IE10包括以上都可以正常使用CORS

##### JSONP

> 原理 script标签跨域不会被阻止,加载跨域文件
>
> // 服务器准备好服务器接口
>
> 手动加载JSONP接口或动态加载JSONP接口
>
> const srcipt = document.createElement("script");
>
> script.src = 'https://cbc.com/cns/cncia';
>
> doucunment.body.appChild(script)  // 放入script标签
>
> 声明函数
>
> cosnt handleRespone = data =>{
>
> consloe.log(data);
>
> }
>
> //  <script src="cbahvna.com"></script>

### XHR

#### XHR的属性

##### responseText:文本形式响应

##### responseType:设置响应类型

##### timeout属性

// 设置请求的超过时间

![image-20230517175626990](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20230517175626990.png)

##### withCredentials 属性

指定使用Ajax发送请求时是否携带Cookie

使用Ajaz发送请求时，默认情况下，同域时，会携带Cookie，跨域时不会

// xhr.withCredentials = true ;

// 呢能否最终成功跨域携带Cookie要看服务器是否同意

#### XHR的方法

// 全为 IE10 后支持

##### abort()  

// 终止当前请求  在发送请求(  xhr.send();   xhr.abort())之后

##### setRequestHeader()

// 可以设置头信息  

在准备好(xhr.open('POST'))后     // 必须是POST请求

 setRequestHeader('Content-Type','balabala')  

 // 也可以使用Content-Type 用于告诉服务器 浏览器发送的数据是什么格式  对应send里面传的值   enctype(在title标签)也可以设置  

发送(xhr.send)前

#### XHR的事件

##### load事件

> 响应数据可用时触发

监听事件时    // 不支持IE6~8 也可以通过 addEventListener()监听 

![image-20230517181948394](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20230517181948394.png)

##### error事件

> 请求(open())发生错误时触发 

与else erro不同  else中是发生响应的

![image-20230517182539485](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20230517182539485.png)

abort事件

> 终止当前请求  在发送请求(  xhr.send();   xhr.abort())之后

![image-20230517182716830](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20230517182716830.png)

timeout事件  // IE8后支持

> 请求超时后触发

![image-20230517182921277](C:\Users\ASUS\AppData\Roaming\Typora\typora-user-images\image-20230517182921277.png)