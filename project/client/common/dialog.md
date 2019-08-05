# 公共弹窗

## 关于平台弹窗
  * 传入参数  
```py
{
	"title" : "关于", # 弹窗标题
	"size" : (-1,-1), # 弹窗大小
	"style" : wx.DEFAULT_DIALOG_STYLE, # 弹窗风格
	"focusUrlColor" : wx.Colour(0,128,255), # 聚焦官网url文本时的颜色
}
```
  * 版本号：`AppConfig中的version字段`
  * 官网网址`AppConfig中的PyToolsIPUrl字段`


## 添加本地工具弹窗
  * 传入参数  
```py
{
	"title" : "添加本地工具", # 弹窗标题
	"size" : (-1,-1), # 弹窗大小
	"style" : wx.DEFAULT_DIALOG_STYLE, # 弹窗风格
	"baseCategory" : "本地工具", # 本地工具的默认分类
	"checkToolKey" : None, # 检测工具key值的回调
	"dirInput" : { # 文件夹输入框
		"name" : "工具路径",
	},
	"name" : {
		"label" : "工具名称",
		"onBlur" : None, # 失焦时的回调
	},
	"category" : {
		"label" : "工具名称",
		"onBlur" : None, # 失焦时的回调
	},
	"description" : {
		"label" : "工具名称",
		"onBlur" : None, # 失焦时的回调
		"inputSize" : (-1, 100), # 输入框尺寸
	},
}
```

## 下载进度弹窗
  * 传入参数  
```py
{
	"title" : "下载", # 弹窗标题
	"size" : (-1,-1), # 弹窗大小
	"style" : wx.DEFAULT_DIALOG_STYLE, # 弹窗风格
	# "pos", (0,0), # 弹窗位置
}
```

## 登录弹窗
  * 传入参数  
```py
{
	"title" : "用户登录",
	"size" : (-1,-1),
	"style" : wx.DEFAULT_DIALOG_STYLE,
	"name" : {
		"label" : "用户名",
		# "onInput" : None,
		"onBlur" : None,
	},
	"password" : {
		"label" : "密码",
		# "onInput" : None,
		"onBlur" : None,
	},
	"onOk" : None, # 点击确认按钮的回调函数
}
```

## 注册弹窗
  * 传入参数  
```py
{
	"title" : "用户注册",
	"size" : (-1,-1),
	"style" : wx.DEFAULT_DIALOG_STYLE,
	"name" : {
		"label" : "用户名",
		# "onInput" : None,
		"onBlur" : None,
	},
	"email" : {
		"label" : "邮箱",
		# "onInput" : None,
		"onBlur" : None,
	},
	"password" : {
		"onBlur" : None,
	},
	"veriCode" : {
		"name" : "邮箱验证",
		"onBlur" : None,
		"onBtn" : None,
	},
	"onOk" : None, # 点击确认按钮的回调函数
}
```

## 工具开发弹窗
  * 传入参数  
```py
{
	"title" : "工具开发",
	"size" : (300, 200),
	"name" : "工具名称",
	"dirName" : "工程路径",
	"textCtrlSize" : (-1, 20),
}
```

## 工具信息弹窗
  * 传入参数  
```py
{
	"title" : "【%s】"%params.get("name", "标题"),
	"size" : (300,-1),
	"style" : wx.DEFAULT_DIALOG_STYLE,
	"name" : "工具名",
	"path" : "--",
	"version" : "--",
	"author" : "--",
	"description" : {
		"height" : 120,
		"value" : "",
	},
	"download" : {
		"label" : "已是最新版本",
		"isUpdate" : False, # 是否更新的标记
		"onDownload" : None, # 下载回调
		"checkDownload" : None, # 检测是否下载
	},
}
```

## 上传工具弹窗
  * 传入参数  
```py
{
	"title" : "上传工具包",
	"size" : (-1,-1),
	"style" : wx.DEFAULT_DIALOG_STYLE,
	"dirInput" : {
		"name" : "工具路径",
		"buttonLabel" : "选择目录",
	},
	"name" : {
		"label" : "工具名称",
		"onBlur" : None,
	},
	"onlineVersion" : {
		"name" : "线上版本",
	},
	"version" : {
		"label" : "工具版本",
		"onBlur" : None,
	},
	"conmonVersion" : {
		"name" : "IP版本",
	},
	"description" : {
		"label" : "工具简介",
		"onBlur" : None,
		"inputSize" : (-1, 100),
	},
	"category" : {
		"label" : "工具分类",
		"choicesInfo" : {}, # 选项信息
	},
	"exCategory" : {
		"label" : "扩展分类",
		"onBlur" : None,
	},
}
```