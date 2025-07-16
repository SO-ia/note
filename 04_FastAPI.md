## configuration

### Installation

```powershell
pip installl fastapi uvicorn
```

#### test

```python
from fastapi import FastAPI

app = FastAPI()
```

##### run command

```powershell
uvicorn 00-test:app --reload --host 8000
uvicorn interface:app --reload --host 8000
```

##### output

```powershell
INFO:     Will watch for changes in these directories: ['D:\\A_Project\\2_fastapi']
INFO:     Uvicorn running on http://127.0.0.1:8000 (Press CTRL+C to quit)
INFO:     Started reloader process [28952] using StatReload
INFO:     Started server process [27840]
INFO:     Waiting for application startup.
INFO:     Application startup complete.
```

##### 访问 [127.0.0.1:8000](http://127.0.0.1:8000/)

```powershell
INFO:     127.0.0.1:55963 - "GET / HTTP/1.1" 404 Not Found
```

##### 访问接口文档

http://127.0.0.1:8000/docs

```powershell
INFO:     127.0.0.1:55964 - "GET /docs HTTP/1.1" 200 OK
INFO:     127.0.0.1:55964 - "GET /openapi.json HTTP/1.1" 200 OK
```

##### 接口测试

```python
from fastapi import FastAPI

app = FastAPI()

@app.get('/')
async def index():
    return {}
```





## Error

### 1 uvicorn 启动错误

#### error

```powershell
uvicorn interface:app --reload --host 8000

# 运行报错：
ERROR:    [Errno 99] Cannot assign requested address
```

#### cause

IP 地址配置问题：

`0.0.0.0` 作为主机地址，表示监听所有网络接口上的连接



#### solution

```powershell
uvicorn interface:app --reload --host 0.0.0.0 --port 8000
```

服务可以接受来自任何 IP 地址的连接请求





### 2 

#### error

```powershell
ValueError: [TypeError("'coroutine' object is not iterable"), TypeError('vars() argument must have __dict__ attribute')]
```

#### solution

在fastapi ，uvloop使用异步函数
使用异步的时候 ‘coroutine’ object is not iterable错误
原来发现，是同步函数中调用异步代码，

请在外面函数中加上async ,await

```python
async def fetch_data():
    return "data"
 
async def main():
    data = await fetch_data()  # 正确使用await来获取结果
    for d in data:  # 现在data是字符串，可以迭代
        print(d)
 
# 运行主函数
import asyncio
asyncio.run(main())
```

> https://blog.csdn.net/asd52656/article/details/118440865