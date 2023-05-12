## Cookie

> 浏览器存储数据的一种方式，存储在用户本地而不是服务器。
>
> 自动随着浏览器每次请求发送到服务器

#### 用途

> 跟踪统计用户访问该网站的习惯。例如时常，停留时间，访问页面

在浏览器操作

#### 基本用法

##### 写入Cookie

> document.cookie = '12345';   //只能一个一个设置

##### 读取Cookie

> console.log(document.cookie);   //一个分号和空格隔开

#### 属性

名称(name)和值(value)    //必须写入其他可以使用默认值

>  如果名称或值包含非英文字母，则写入时需要 encodeURIComponent() 编码，读取时使用decodeURIComponent()解码 
>
> 例如: 
>
> documnet.cookie = `username=${encodeURIComponent('zhansan')}`;
>
>   documnet.cookie = `${encodeURIComponent('用户名')}=${encodeURIComponent('zhangsan ')}`;    // 一般使用英文。

#### 失效(到期)事件

对于失效的Cookie，会被浏览器清除。

没有设置内销事件，这样的Cookie成为会话Cookie,当会话结束(浏览器关闭)，Cookie消失。 

> 想要长时间存在，设置Expires或Max-Age
>
> documnet.cookie = \` username = alex;expires=${new Date(时间)} \`  // expires
>
> document.cookie = \`username = \`username=alex;Max-age=5\`;    
>
> document.cookie = \`username = \`username=alex;max-age=${24*360}\`;    // 当前时间+多少秒后过期单位是秒,Max-Age是0或复数Cookie将被删除

#### Domain域

Domain限制(不同域名)Cookie范围

document.cookie = 'username = ale;domain=路径';    // 只能续写父域

#### Path 路径

Path限制(相同域名)Cookie范围  // 无法写入下一级路径 可写入 当前和上一级路径

#### HttpOnly

设置了HttpOnly属性  Cookie不能通过JS去访问

#### Secure安全标志

Secure限定只有在使用了https而不是http的情况下可以发送给服务器

#### 封装

封装Cookie

```javascript
    export const set = (name,value,{maxAge,domain,path,secure}={}) => {

    let cookieText = `${encodeURIComponent(name)}=${encodeURIComponent(value)}`;

    if(typeof maxAge==='number'){
        cookieText += `;max-age=$(maxAge)`;
    }

    if(domaine){
        cookieText += `;domain=$(domain)`;
    }

    if(path){
        cookieText += `;path=$(path)`;
    }

    if(tsecure){
        cookieText += `;secure=$(secure)`;
    }

    }
```

#### 注意事项

1.前后端都可以创建Cookie

2.Cookie有数量限制(每个域下)

3.Cookie有大小限制
