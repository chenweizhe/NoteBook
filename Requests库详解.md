### Requests库详解

---

#### 什么是Requests库

>基于urllib，采用Apache2 Licensed开源协议的HTTP库
>
>比urllib更方便，节约大量工作，满足http测试需求

#### 请求方式

```
import requests
requests.post('http://httpbin.org/post')
requests.put('http://httpbin.org/put')
requests.delete('http://httpbin.org/delete')
requests.head('http://httpbin.org/get')
requests.options('http://httpbin.org/get')
```

#### get请求

```python
import requests

response = requests.get('http://httpbin.org/get')

print(response.text)

# 带参get请求

response = requests.get('http://httpbin.org/get?name=germey&age=22')
print(response.text)
import requests
data = {
    'name':'germey',
    'age':22
}
response = requests.get('http://httpbin.org/get',params=data)
print(response.text)
```

#### json解析

```python
# json解析

import requests
import json

response = requests.get('http://httpbin.org/get')

print(type(response.text))

print(response.json)
print(json.loads(response.text))

print(type(response.json))
```

>response.json实际上就是执行了json.loads方法

#### 获取二进制数据

```python
import requests 
response = requests.get('https://www.github.com/favicon.ico')
print(type(response.text),type(response.content))
print(response.text)
print(response.content)
```

#### 添加headers

```python
import requests

response = requests.get('https://www.zhihu.com/explore')
print(response.text)

headers = {
     'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/52.0.2743.116 Safari/537.36'
}
response = requests.get('https://www.zhihu.com/explore',headers=headers)
print(response.text)
```



#### post请求

```python
data = {'name':'germey','age':'22'}

headers = {
    'User-Agent': 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/52.0.2743.116 Safari/537.36'
}
response = requests.post('http://httpbin.org/post',data=data,headers=headers)
print(response.json)

```

#### 响应

```Python
response = requests.get('http://www.jianshu.com/hello.html')
exit() if not response.status_code == 200 else print('ok')
```

---

### 高级用法

#### 文件上传

```Python
import requests

files = {'file':open('favicon.ico','rb')}

response = requests.post('http://httpbin.org/post',files=files)
print(response.text)
```



#### 获取cookie

```Python
import requests
response = requests.get('https://www.baidu.com')

print(response.cookies)
for key,value in response.cookies.items():
    print(key+'='+value)'''
```



#### 会话维持，可用于模拟登录

```python
import requests

requests.get('http://httpbin.org/cookies/set/number/123456789')
response = requests.get('http://httpbin.org/cookies')
print(response.text)	
```



#### 证书验证

```python
import requests 
from requests.packages import urllib3
urllib3.disable_warnings()
response = requests.get('https://www.12306.cn',verify=False)
print(response.status_code)
```



#### 超时设置

```python
import requests 
from requests.exceptions import ReadTimeout
try:
    response = requests.get('http://httpbin.org/get',timeout=0.5)
    print(response.status_code)
except ReadTimeout:
    print('time out')
```

#### 认证设置

```python
import requests 
from requests.auth import HTTPBasicAuth

r = requests.get('http://120.27.34.24:9001', auth=HTTPBasicAuth('user', '123'))
print(r.status_code)
```

#### 异常处理

```python
import requests 
from requests.exceptions import ReadTimeout,ConnectionError,RequestException
try:
    response = requests.get('http://httpbin.org/get',timeout=0.5)
    print(response.status_code)
except ReadTimeout:
    print('timeout')

except ConnectionError:
    print('connection error')
except RequestException:
    print('error')
```

