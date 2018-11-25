# TCP编程

### 客户端
```python
import socket

# 创建一个socket并建立连接
s_client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s_client.connect(('127.0.0.1', 8888))

# 接收欢迎消息
print(s_client.recv(1024).decode('utf-8'))

# 发送数据并接收服务器返回的数据
for data in [b'Michael', b'Tracy', b'Sarah']:
    s_client.send(data)
    print(s_client.recv(1024).decode('utf-8'))

# 客户端退出
s_client.send(b'exit')
s_client.close()
```

### 服务器
```python
import socket, threading, time

def tcplink(sock, addr):
    print('Accept new connection from %s:%s...' % addr)
    sock.send(b'Welcome!')
    while True:
        data = sock.recv(1024)
        time.sleep(1)
        if not data or data.decode('utf-8') == 'exit':
            break
        sock.send(('Hello, %s!' % data.decode('utf-8')).encode('utf-8'))
    sock.close()
    print('Connection from %s:%s closed.' % addr)


# 创建一个基于IPv4和TCP的socket
s_server = socket.socket(socket.AF_INET, socket.SOCK_STREAM) 

# 绑定监听的地址和端口
s_server.bind(('127.0.0.1', 8888))

# 监听端口
s_server.listen(5)
print('Waiting for connection...')

# 接收来自客户端的连接，并创建新线程来处理tcp连接
while True:
    sock, addr = s_server.accept()
    t = threading.Thread(target=tcplink, args=(sock, addr))
    t.start()
```
