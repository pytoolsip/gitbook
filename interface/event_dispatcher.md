# 事件分发器

----
## 1. 事件分发意义
不同模块之间可通过分发事件的方式，相互调用逻辑处理接口，在保证功能性的前提下，减少了模块之间逻辑的耦合性，使得代码结构清晰，易于理解。

## 2. 机制实现
这里采用一般的实现方式：  
  * 首先，创建一个全局变量（保证在工程中的每个模块都能拿到）作为事件管理器；
  * 其次，创建事件`ID`的相关配置文件，允许开发者新建`ID`配置；
  * 开发者在代码中，通过调用事件管理器的注册事件接口进行事件注册，而事件管理器则会将该注册信息保存当前运行内存中；
  * 开发者在代码中，通过调用事件管理器的分发事件接口进行事件分发，而事件管理器则会根据之前的注册信息，调用相应的回调函数；
  * 最后，开发者在销毁某个注册了事件的类时，必须要注销之前的注册事件，否则会出现调用销毁对象的方法而抛错问题。

## 3. 用法
### 3.1 新增事件ID
#### 3.1.1 新增事件ID配置
在工具中新增事件`ID`配置（一般在`assets/tool/config`文件夹下新增`EventId.py`文件），如下所示：
```py
from enum import Enum, unique;

from _Global import _GG;

# 枚举事件Id
@unique
class EVENT_ID(Enum):
	KEY_LEFT_EVENT = _GG("EVENT_ID").getNewId(); # 键盘键【左】

	KEY_UP_EVENT = _GG("EVENT_ID").getNewId(); # 键盘键【上】

	KEY_RIGHT_EVENT = _GG("EVENT_ID").getNewId(); # 键盘键【右】

	KEY_DOWN_EVENT = _GG("EVENT_ID").getNewId(); # 键盘键【下】
```

#### 3.1.2 更新common的事件ID
在工具的`_loadtool.py`文件中，添加以下代码：
```py
# 以下进行初始化逻辑，如初始化事件ID和热键配置

# 加载事件ID
EventId = require(GetPathByRelativePath("config", CURRENT_PATH), "EventId", "EVENT_ID");

# 更新配置
_GG("EventDispatcher").updateEventIds();
```

### 3.2 注册事件
通过调用以下的语句来注册事件。其中`_GG`为全局包。
```py
_GG("EventDispatcher").register(eventId, object, callbackName);
```

### 3.3 注销事件
通过调用以下的语句来注销事件。
```py
_GG("EventDispatcher").unregister(eventId, object, callbackName);
```

### 3.4 分发事件
通过调用以下的语句来注销事件。其中data是字典类型的数据。
```py
_GG("EventDispatcher").dispatch(eventId, data);
```