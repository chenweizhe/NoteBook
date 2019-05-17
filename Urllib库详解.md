#### Urllib库详解

---

> python内置的http请求库

| 名称               | 功能              |
| ------------------ | ----------------- |
| urllib.request     | 请求模块          |
| urllib.error       | 异常处理模块      |
| urllib.parse       | url解析模块       |
| urllib.robotparser | robot.txt解析模块 |

#### urlopen

```python
urllib.request.urlopen(url, data=None, [timeout, ]*, cafile=None, capath=None, cadefault=False, context=None)
```

```python
#! /usr/bin/env python3
#get类型的请求
import urllib.request 
response = urllib.request.urlopen('http://www.baidu.com')
print(response.read().decode('utf-8'))
```

```Python
import urllib.parse
# post请求
data = bytes(urllib.parse.urlencode({'word':'hello'}),encoding='utf-8')
response = urllib.request.urlopen('http://httpbin.org/post',data=data)
print('dai')
print(response.read())

```

> 设置请求响应时间，超出请求响应时间，返回异常
>
> ```python
> import urllib.error
> import socket
> try:
>     response = urllib.request.urlopen('http://httpbin.org/get',timeout=0.1)
> except urllib.error.URLError as e:
>     if isinstance(e.reason,socket.timeout):
>         print('TIME OUT')
> ```

#### 响应

> ##### 响应类型、状态码、响应头
>
> ```python
> response = urllib.request.urlopen('https://www.python.org')
> print(type(response))
> print(response.status)
> print(response.getheaders())
> print(response.getheader('Server'))
> ```
>
> ><class 'http.client.HTTPResponse'>
> >200
> >[('Server', 'nginx'), ('Content-Type', 'text/html; charset=utf-8'), ('X-Frame-Options', 'DENY'), ('Via', '1.1 vegur'), ('Via', '1.1 varnish'), ('Content-Length', '48293'), ('Accept-Ranges', 'bytes'), ('Date', 'Wed, 01 May 2019 08:26:16 GMT'), ('Via', '1.1 varnish'), ('Age', '220'), ('Connection', 'close'), ('X-Served-By', 'cache-iad2142-IAD, cache-tyo19926-TYO'), ('X-Cache', 'HIT, HIT'), ('X-Cache-Hits', '2, 431'), ('X-Timer', 'S1556699176.231668,VS0,VE0'), ('Vary', 'Cookie'), ('Strict-Transport-Security', 'max-age=63072000; includeSubDomains')]
> >nginx

#### Request

> 可以加入请求头信息

```python
request = urllib.request.Request('https://python.org')
response = urllib.request.urlopen(request)
print(response.read().decode('utf-8'))
```

```python
from urllib import request,parse

url = 'http://httpbin.org/post'
headers = {'User-Agent':'Mozilla/4.0 (compatible; MSIE 5.5; Windows NT)',
            'Host':'httpbin.org'
}

dict = {
    'name':'Germey'
}
data = bytes(parse.urlencode(dict),encoding='utf8')
req = request.Request(url=url,data=data,headers=headers,method='POST')
response = request.urlopen(req)
print(response.read().decode('utf-8'))
```

#### Handler

- 代理

- cookie

  ```python
  import http.cookiejar
  
  cookie =http.cookiejar.CookieJar()
  
  handler = urllib.request.HTTPCookieProcessor(cookie)
  
  opener = urllib.request.build_opener(handler)
  response = opener.open('http://www.baidu.com')
  
  for item in cookie:
      print(item.name+'='+item.value)
  ```

  ```python
  import http.cookiejar,urllib.request
  
  filename = 'cookie.txt'
  cookie = http.cookiejar.MozillaCookieJar(filename)
  handler = urllib.request.HTTPCookieProcessor(cookie)
  
  opener =  urllib.request.build_opener(handler)
  response = opener.open('http://www.baidu.com')
  cookie.save(ignore_discard=True,ignore_expires=True)
  ```

#### 异常处理

```
import socket

try:
    response = urllib.request.urlopen('https://www.baidu.com',timeout=0.01)

except urllib.error.URLError as e:
    print(type(e.reason))
    if isinstance(e.reason,socket.timeout):
        print('time out')
```

#### URL解析

- urlpase (切分url请求)

  ```python
  import urllib.parse
  
  result = urllib.parse.urlparse('http://www.baidu.com/index.html;user?id=5#comment')
  print(type(result),result)
  ```

  ```
  
  from urllib.parse import urlparse
  result = urlparse('www.baidu.com/index.html;user?id=5#comment',allow_fragments=True)
  
  print(result)
  ```

  

- urlunparse（将元素拼接成一条url请求）

- urljion（拼接两条url请求）

- urlencode（将字典转化为get请求）

  ```python
  from urllib.parse import urlencode
  
  params = {
      'name': 'germey',
      'age': 22
  }
  
  base_url  = 'http://www.baidu.com'
  url = base_url+urlencode(params)
  
  print(url)
  ```

  

- robotparser（解析robots.txt文件）

  

  

  