## 跨域
跨域是浏览器的安全策略
同源策略：同协议 域名 端口
不同源 存在跨域



## CORS
规定了一组 http 的头部字段作用是：
允许哪些网站通过浏览器有访问的权限
1. access-X
2. cookie
3. 浏览器会先以OPTIONS请求方法发起一个预检(preflight)请求，获取一下允不允许当前的请求，服务器允许之后才会发起正式的请求

## 代理
1. Nginx
   反向代理：live-server --proxy=/api:http://localhost:9999/api/
   不知道请求的是哪个服务器
   正向代理：
   Google
   A -> proxy -> google.com
   B -> proxy -> google.com

## iframe + postMessage
1. 前端页面 通过iframe引入一个后端目录下面的html
   iframe 是不受同源策略限制的，
2. postMessage用于在两个窗口之间的数据传递
3. 前端页面 通过 postMessage 向后端目录下的面的html传递接口需要的请求参数
4. 后端页面通过postMessage向前端页面传递接口结果

## iframe + window.name
iframe 共享 window.name

没有 postMessage 只能借助中间页面通知前端页面 window.parent.callback(window.name)

## jsonp
1. 定义一个回调
2. 将回调函数的名字告诉后端 后端会返回
   ```js
   回调(res)
   ```
3. script 标签加载过后执行返回的内容
   写一个jsonp的函数，以promise的方式调用
   json(url)
   .then(res => {

   })

缺点： 只能发起get请求