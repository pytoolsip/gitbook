# 服务端组件

## 平台信息（IPInfoBehavior）
  * 依赖组件  
```py
{
	"path" : "ConfigParseBehavior/IniConfigParseBehavior",
	"basePath" : _GG("g_CommonPath") + "behavior/",
}
```

  * 导出接口  
```py
# 获取平台信息配置对象
# @return object ini配置对象
getIPInfoConfigObj();

# 获取平台信息配置对象
# @params section ini配置的section
# @params option ini配置的option
# @return string 对应ini配置section下option的值
getIPInfoConfig(section, option);

# 设置平台信息配置
# @params section ini配置的section
# @params option ini配置的option
# @params value ini配置对应section和option的值
setIPInfoConfig(section, option, value);

# 设置平台信息配置
# @params section ini配置的section
# @params option ini配置的option【可选】
removeIPInfoConfig(section, option = None);
```

## 基础服务（ServiceBehavior）
  * 依赖组件  
```py
{
	"path" : "serviceBehavior/UpDownloadBehavior",
	"basePath" : _GG("g_CommonPath") + "behavior/",
},
{
	"path" : "serviceBehavior/IPInfoBehavior",
	"basePath" : _GG("g_CommonPath") + "behavior/",
}
```

  * 导出接口  
```py
# 检测更新平台
checkUpdateIP();

# 自动登录平台
autoLoginIP();
```

## 工具服务（ToolServiceBehavior）
  * 依赖组件  
```py
{
	"path" : "serviceBehavior/UpDownloadBehavior", 
	"basePath" : _GG("g_CommonPath") + "behavior/",
}
```

  * 导出接口  
```py
# 上传工具
_uploadTool_();

# 显示工具信息
# @params data 工具数据
_showToolInfo_(data);

# 下载工具
_downloadTool_();
```

## 上传及下载（UpDownloadBehavior）
  * 导出接口  
```py
# 下载文件
# @params url 下载地址
# @params filePath 下载到本地的路径
# @params totalSize 下载本地大小
# @params onComplete 下载完成后的回调
download(url, filePath, totalSize, onComplete = None);

# 上传文件
# @params filePath 上传文件路径
# @params data 上传数据
#	host 主机IP
#	port 端口
#	user 用户名
#	password 密码
#	url 保留到远程的路径
upload(filePath, data);

# 压缩文件
# @params dirpath 源文件路径
# @params filePath 压缩后的文件路径
# @params finishCallback 压缩完成后的回调
zipFile(dirpath, filePath, finishCallback = None);

# 解压文件
# @params filePath 压缩文件路径
# @params dirpath 压缩后的路径
# @params finishCallback 压缩完成后的回调
unzipFile(filePath, dirpath, finishCallback = None);
```

## 用户服务（UserServiceBehavior）
  * 依赖组件  
```py
{
	"path" : "serviceBehavior/IPInfoBehavior", 
	"basePath" : _GG("g_CommonPath") + "behavior/",
}
```

  * 导出接口  
```py
# 登录平台
_loginIP_();

# 注册平台
_registerIP_();

# 登出平台
_logoutIP_();
```