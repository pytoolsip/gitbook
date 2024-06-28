# 通用函数

----
## 1. 基础函数
主要提供了平台工程的常用接口，以及对一些操作（如销毁基于平台工程的对象）进行封装管理，以达到正确加载和销毁等目的。  

### 1.1 动态加载模块
**`require(filePath, moduleName, subModuleName = None, isReload = False, isReserve = False, modulePathBase = "")`**  

参数：  
  * filePath : 模块文件路径
  * moduleName : 模块名
  * subModuleName : 子模块名
  * isReload : 是否重新加载
  * isReserve : 是否保留先前加载过的同名模块
  * modulePathBase : 模块路径的基础路径

返回值：
  * object : 模块对象


### 1.2 根据相对路径获取路径
**`GetPathByRelativePath(path, basePath = "")`**  

参数：
  * path : 相对路径
  * basePath : 基础路径

返回值：
  * string : 绝对路径


### 1.3 创建控制类（视图或窗口）
**`CreateCtr(path, parent, params = {}, isReload = False, isReserve = False)`**  

参数：
  * path : 模块路径
  * parent : 父节点
  * params : 初始化参数
  * isReload : 是否重新加载
  * isReserve : 是否保留先前加载过的同名模块

返回值：
  * object : 模块对象


### 1.4 销毁控制类【需先销毁UI】（视图或窗口）
**`DelCtr(ctr)`**  

参数：
  * ctr : 模块对象

### 1.5 主动销毁类
**`Del(obj)`**  

参数：
  * obj : 模块对象


### 1.6 校验路径
**`VerifyPath(path)`**  

参数：
  * path : 路径


### 1.7 检测版本
**`CheckVersion(v1, v2, isCheckFirst = True, isIncludeEqu = False)`**  

参数：
  * v1 : 版本1
  * v2 : 版本2
  * isCheckFirst : 是否检测第一位版本号
  * isIncludeEqu : 是否包含相同版本的检测结果

返回值：
  * boolean : 版本1 > 版本2 or (版本1 == 版本2 and isIncludeEqu)


### 1.8 获取基础版本（前两位版本号）
**`GetBaseVersion(version)`**  

参数：
  * version : 版本号
  

### 1.9 无日志打印的运行命令
**`RunCmd(cmd, cwd=os.getcwd(), funcName="call", argDict = {})`**  

参数：
  * cmd : 运行命令
  * cwd : 运行路径（默认是当前路径）
  * funcName : 调用子进程的函数名称
  * argDict : 调用子进程的其他参数

返回值：
  * int : 运行结果码


## 2. 线程扩展函数
### 2.1 停止线程
**`stopThread(thread)`**  

参数：
  * thread : 线程对象


## 3. 随机函数
### 3.1 随机字母和数字
**`randomMulti(length)`**  

参数：
  * length : 长度

返回值：
  * string : 随机值


### 3.2 随机字母
**`randomStr(length)`**  

参数：
  * length : 长度

返回值：
  * string : 随机值


### 3.3 随机数字
**`randomNum(length)`**  

参数：
  * length : 长度

返回值：
  * string : 随机值