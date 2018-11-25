# WSGI实现最简单的web编程

### WSGI app
```python
def application(environ, start_response):
    start_response('200 OK', [('Content-Type', 'text/html')])
    body = 'Hello, %s!' % (environ['PATH_INFO'][1:] or 'world')
    return [body.encode('utf-8')]
```

### WSGI server
```python
from wsgiref.simple_server import make_server
from hello import application

'''
启动WSGI服务器，加载application()函数
'''

# 创建一个服务器，IP地址为空，端口是8000，处理函数是application
httpd = make_server('', 8000, application)
print('Serving HTTP on port 8000...')
# 开始监听HTTP请求
httpd.serve_forever()
```
