#### 一、HTTP 请求
##### 1. http请求操作/curl命令
- ` curl -s -v -H "Frank: xxx" -- "https://www.baidu.com"//GET获取操作`
请求内容:
```
GET / HTTP/1.1
Host: www.baidu.com
User-Agent: curl/7.54.0
Accept: */*
Frank: xxx


```
- `curl -X POST -s -v -H "Frank: xxx" -- "https://www.baidu.com"//POST上传操作`

请求内容:
```
POST / HTTP/1.1
Host: www.baidu.com
User-Agent: curl/7.54.0
Accept: */*
Frank: xxx


```
- `curl -X POST -d "1234567890" -s -v -H "Frank: xxx" -- "https://www.baidu.com"//POST上传带数据`
请求内容
```
POST / HTTP/1.1
Host: www.baidu.com
User-Agent: curl/7.54.0
Accept: */*
Frank: xxx
Content-Length: 10
Content-Type: application/x-www-form-urlencoded

1234567890
```

##### 2. 综上所得，请求一共包含以下部分
- 1 动词 路径 协议/版本

    2 Key1: value1

    2 Key2: value2

    2 Key3: value3

    2 Content-Type: application/x-www-form-urlencoded

    2 Host: www.baidu.com

    2 User-Agent: curl/7.54.0

    3 

    4 要上传的数据
###### 其中，

（1）请求最多包含四部分，最少包含三部分，即第四部分数据可以为空。

（2）第三部分永远都是一个回车，用来分隔第二、第四部分。

（3）第一部分的动词包括GET（获取）/POST（上传，新增）/PUT（整体更新）/PATCH（局部更新）/DELETE（删除）/HEAD（获取资源的元数据）/OPTIONS（获取信息，关于资源的哪些属性是客户端可以改变的）等。

（4）如果没有写路径，则默认为根目录（即 /）

（5）第二部分中的的 Content-Type 标注了第 4 部分的格式

（6）第一部分的路径，包含查询参数，但不包括锚点

#### 3. 使用Chrome浏览器查看http请求
打开 Network
地址栏输入网址
在 Network 点击，查看 request，点击「view source」
如果有请求的第四部分，那么在 FormData 或 Payload 里面可以看到
![百度首页请求](https://upload-images.jianshu.io/upload_images/11827773-64f499129a9c15f5.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)




#### 二、HTTP 响应
#### 1.http响应出现在请求结束后
如`curl -s -v -H "Frank: xxx" -- "https://www.baidu.com"//GET获取操作`
获得的响应代码为：
```
HTTP/1.1 200 OK
Accept-Ranges: bytes
Cache-Control: private, no-cache, no-store, proxy-revalidate, no-transform
Connection: Keep-Alive
Content-Length: 2443
Content-Type: text/html
Date: Tue, 10 Oct 2017 09:14:05 GMT
Etag: "5886041d-98b"
Last-Modified: Mon, 23 Jan 2017 13:24:45 GMT
Pragma: no-cache
Server: bfe/1.0.8.18
Set-Cookie: BDORZ=27315; max-age=86400; domain=.baidu.com; path=/

<!DOCTYPE html>
………………以下为网页html代码，略…………
```
#### 2. http响应包含以下部分
- 1 协议/版本号 状态码 状态解释

    2 Key1: value1

    2 Key2: value2

    2 Content-Length: 17931

    2 Content-Type: text/html

    3

    4 要下载的内容
###### 其中，
第 2 部分中的 Content-Type 标注了第 4 部分的格式
第 2 部分中的 Content-Type 遵循 MIME 规范
第一部分的状态解释没什么用
#### 3. 关于响应的状态码
- 1xx 消息
- 2xx 表示成功

    200 表示普通成功（如GET获取时）

    204 表示创建成功（如POST提交时）
- 3xx 表示重定向

    301 表示所访问的资源永久被移除

    302 表示所访问的资源临时被移除，以后还会回来

    304 表示资源未被修改，即客户端仍然具有以前下载的副本，不需要重新传输资源
- 4xx 表示客户端错误

    404  请求所希望得到的资源未被在服务器上发现，但允许用户的后续请求
- 5xx 表示服务器错误

    502 上游服务器接收到无效的响应

#### 4. 使用Chrome浏览器查看http响应
打开 Network
输入网址
选中第一个响应
查看 `Response Headers` ，点击`「view source」`
你会看到响应的前两部分
查看 `Response` 或者 `Preview`，你会看到响应的第 4 部分
![百度首页响应代码](https://upload-images.jianshu.io/upload_images/11827773-a69411105b833e6b.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

