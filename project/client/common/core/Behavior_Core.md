# 组件机制

## 组件的意义
组件的主要意义在于，将**高复用性、功能单一且独立（低依赖）**的代码，进行抽离封装。  
从而，减少冗余代码，且使用方便。开发人员可以通过绑定组件，调用相关接口来使用相应功能，而不必重复编码。  
而在模块功能扩展方面，组件化的设计允许开发人员，在不改变原有逻辑的基础上，通过增加或改变组件的绑定，来进行功能扩展或修改。  

## 组件机制实现
### 组件基本结构
```
# BaseBehavior

from enum import Enum, unique;
from _Global import _GG;

# 枚举执行类型
@unique
class DoType(Enum):
	AddToFront = 0; # 前置添加
	Override = 1; # 覆盖/覆写
	AddToRear = 2; # 后置添加

class BaseBehavior(object):
	def __init__(self, depends = []):
		super(BaseBehavior, self).__init__();
		self.className_ = BaseBehavior.__name__;
		self.DependBehaviorList_ = depends; # 依赖组件列表
		self.BeDependedBehaviorList_ = []; # 被依赖组件列表

	# 打印obj绑定的组件名称【obj为绑定该组件的对象，argList和argDict为可变参数】
	def printBehaviorName(self, obj, *argList, **argDict):
		print(self.className_);
		pass;

	# 设置组件Id
	def setBehaviorId(self, bid):
		self.behaviorId_ = bid;

	# 获取组件导出数据
	def getBehaviorExposeData(self):
		baseExposeData = {};
		exposeData = self.getExposeData(); # 获取暴露出的数据
		for dataKey,dataValue in baseExposeData.items():
			if dataKey not in exposeData:
				exposeData[dataKey] = dataValue;
		return exposeData;

	# 获取组件导出方法
	def getBehaviorExposeMethod(self):
		baseExposeMethod = {"printBehaviorName" : DoType.AddToRear};
		exposeMethod = self.getExposeMethod(DoType); # 获取暴露出的方法接口
		for methodName,methodType in baseExposeMethod.items():
			if methodName not in exposeMethod:
				exposeMethod[methodName] = methodType;
		return exposeMethod;
```
主要函数或数据说明：
  * DoType : 枚举类型数据。方法绑定时的类型配置，分为前置绑定（`AddToFront`）、覆盖绑定（`Override`）和后置绑定（`AddToRear`）。
  * self.DependBehaviorList_ : 组件的依赖组件列表。对于需要依赖其他组件的组件，在初始化该组件时，需要传入所依赖的组件到构造函数中，从而可以使用所依赖组件的功能。
  * self.BeDependedBehaviorList_ : 组件被依赖组件列表（value为被依赖组件的组件Id）。
  * self.printBehaviorName() : 测试接口，用于打印相应对象所绑定的所有组件名。
  * 其他函数 : 在组件的绑定和解绑过程中，会使用这些接口，一般情况下，用户不会也不能修改这些接口函数，否则会导致绑定或解绑组件出现问题。

### 组件绑定
#### 组件绑定信息保存
由于组件是绑定到对象上的，所以组件的绑定信息保存于相应对象上。  
在此处的组件设计里，组件绑定主要分为数据绑定（较少使用）和方法绑定，因而对应的绑定信息主要保存到对象的`behavior_exposeDataDict__`和`behavior_exposeMethodDict__`字段上。  

#### 组件模板
```
# TemplateBehavior
from _Global import _GG;
from function.base import *;

def getExposeData():
	return {
		# "exposeDataName" : {},
	};

def getExposeMethod(DoType):
	return {
		# "defaultFun" : DoType.AddToRear,
	};

class TemplateBehavior(_GG("BaseBehavior")):
	def __init__(self, depends = []):
		super(TemplateBehavior, self).__init__(depends);
		self.className_ = TemplateBehavior.__name__;
		pass;

	def getExposeData(self):
		return getExposeData(); # 获取暴露出的数据

	def getExposeMethod(self, DoType):
		return getExposeMethod(DoType); # 获取暴露出的方法接口

	# 默认方法【obj为绑定该组件的对象，argList和argDict为可变参数，_retTuple为该组件的前个函数返回值】
	# def defaultFun(self, obj, *argList, _retTuple = None, **argDict):
	# 	print(obj.className_);
	# 	pass;

```
主要函数或数据说明：
  * getExposeData : 组件绑定数据的导出配置。
  * getExposeMethod : 组件绑定方法的导出配置。

#### 组件数据绑定（少用）
在以上组件模板的getExposeData函数中，进行数据配置。当所绑定对象中没有相应字段的数据（包括先前绑定组件的导出数据配置）时，会增加相应字段的数据到对象上。

#### 组件方法绑定
在以上组件模板的getExposeMethod函数中，进行导出函数名配置。在绑定组件时，会将组件中相应函数绑定（前置/覆盖/后置）至对象中的相应方法名，若对象没有相应方法名，则会新增该方法字段到对象上。  
以下就组件方法的三种绑定方式的实用性，进行简要描述。

##### 前置（AddToFront）绑定
一般用于在执行原有对象方法前，进行数据调整，进而实现不同的运行结果。

##### 覆盖（Override）绑定
当一个模块中，需要使用某个对象，而又因其中的某个方法实现不满足需求时，则可以编写含有同名函数的组件，并将方法进行导出。之后在调用模块时，绑定该组件到对象上，待相应逻辑调用完毕后，解绑组件即可。

##### 后置（AddToRear）绑定
一般用于需要对对象的某个方法逻辑进行扩展或后续处理的情景中。


## 组件绑定及使用
### 绑定组件代码
#### 直接绑定/解绑组件
```
# 绑定组件
behavior = _GG("BehaviorManager").bindBehavior(obj, {"path" : "TempBehavior", "basePath" : _GG("g_CommonPath") + "behavior\\"});

# 解绑组件
_GG("BehaviorManager").unbindBehavior(obj, behavior);
```
参数解析：  
  * obj : 组件索要绑定的对象。
  * 第2个参数中的`path` : 组件文件所在的路径。可以通过该路径查找obj上对应的组件。
  * 第2个参数中的`basePath` : 查找组件文件所在路径所基于的路径。

#### 扩展对象操作组件的方法
```
# 绑定组件
behavior = _GG("BehaviorManager").extendBehavior(obj);
obj.bindBehavior({"path" : "temp/TempBehavior", "basePath" : _GG("g_CommonPath") + "behavior\\"});

behaviorId = behavior.getBehaviorId();

# 获取TempBehavior组件【三种方式】
behavior = obj.getBehaviorByName("TempBehavior");
behavior = obj.getBehaviorByPath("temp/TempBehavior");
behavior = obj.getBehaviorById(behaviorId);

# 解绑组件
obj.unbindBehavior(obj, behavior);

```

### 调用组件方法的代码
直接`obj.组件导出方法名`即可。