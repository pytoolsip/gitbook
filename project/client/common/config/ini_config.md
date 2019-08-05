# 基础配置

## 环境配置

```py
[env]
python # 为空的话，默认使用环境变量的python
```

## 服务配置

```py
[server]
host # 服务器IP
port # 服务器端口号
```

## 日志配置

```py
[log]
path = log # 日志文件夹【相对于工程根目录的路径】
name = pytoolsip-client # 日志名称
maxBytes = 102400000 # 单个日志文件的最大尺寸
backupCount = 10 # 最多保留的日志文件个数
```

## 本地配置

```py
[local]
user_info_expire = 864000 # 用户信息的缓存期限
```