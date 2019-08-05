# 扩展ui模块

## 路径输入框控件
参数：  
```py
{
	"size" : (-1,-1),
	"inputSize" : (-1,20),
	"buttonSize" : (30,20),
	"buttonLabel" : "选择",
	"onInput" : None,
}
```

## 扩展输入框
参数：  
```py
{
	"size" : (200,200),
	"name" : "名称",
	"tips" : "*（必填）",
	"exTips" : "提示信息",
	"inputSize" : (-1,20),
	"inputStyle" : wx.TE_PROCESS_TAB,
}
```

扩展方法：
  * onInput : 直接赋值该输入框对象，向输入框输入值时会调用该方法。