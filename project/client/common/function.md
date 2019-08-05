# 基础函数

## 动态加载模块
`require(filePath, moduleName, subModuleName = None, isReload = False, isReserve = False, modulePathBase = "")`  

参数：  
  * filePath : 模块文件路径
  * moduleName : 模块名
  * subModuleName : 子模块名
  * isReload : 是否重新加载
  * isReserve : 是否保留先前加载过的同名模块
  * modulePathBase : 模块路径的基础路径

返回值：
  * object : 模块对象


## 根据相对路径获取路径
`GetPathByRelativePath(path, basePath = "")`  

参数：
  * path : 相对路径
  * basePath : 基础路径

返回值：
  * string : 绝对路径


## 创建控制类（视图或窗口）
`CreateCtr(path, parent, params = {}, isReload = False, isReserve = False, modulePathBase = "")`  

参数：
  * path : 模块路径
  * parent : 父节点
  * params : 初始化参数
  * isReload : 是否重新加载
  * isReserve : 是否保留先前加载过的同名模块
  * modulePathBase : 模块路径的基础路径

返回值：
  * object : 模块对象


## 销毁控制类【需先销毁UI】（视图或窗口）
`DelCtr(ctr)`  

参数：
  * ctr : 模块对象

## 主动销毁类
`Del(obj)`  

参数：
  * obj : 模块对象


## 校验路径
`VerifyPath(path)`  

参数：
  * path : 路径


## 检测版本
`CheckVersion(v1, v2, isCheckFirst = True, isIncludeEqu = False)`  

参数：
  * v1 : 版本1
  * v2 : 版本2
  * isCheckFirst : 是否检测第一位版本号
  * isIncludeEqu : 是否包含相同版本的检测结果

返回值：
  * boolean : 版本1 > 版本1 || isIncludeEqu


## 停止线程
`stopThread(thread)`  

参数：
  * thread : 线程对象