# 热键功能

----
## 1. 意义
尽管可以使用`wx`的机制来直接监控键盘事件，但是为了统一接口函数，这里将部分键盘事件功能抽离出来，作为热键系统进行管理，减少实际编程中增加过多判断代码。

## 2. 机制实现
通过监控`App`对象的`wx.EVT_CHAR_HOOK`事件，获取用户的键盘事件，进而通过热键配置（`common/core/hotKeyCore/HotKeyConfig.py`）中的映射关系，找到相应的事件`ID`，进而通过事件管理器将事件分发到相应对象上。

## 3. 用法
### 3.1 新增自定义事件ID
参考[事件分发器--新增事件ID](event_dispatcher.md#3_1%20新增事件ID)。

### 3.2 新增热键配置
在工具中新增事件`ID`配置（一般在`assets/tool/config`文件夹下新增`HotKeyConfig.py`文件），如下所示：
```py
import os;

from function.base import *;

CurPath = os.path.dirname(os.path.realpath(__file__)); # 当前文件目录
EventID = require(CurPath, "EventId", "EVENT_ID");

# 热键配置
HotKeyConfig = {
	"LEFT" : EventID.KEY_LEFT_EVENT,
	"UP" : EventID.KEY_UP_EVENT,
	"RIGHT" : EventID.KEY_RIGHT_EVENT,
	"DOWN" : EventID.KEY_DOWN_EVENT,
};
```

### 3.3 更新common的热键配置
在工具的`_loadtool.py`文件中，添加以下代码：
```py
# 以下进行初始化逻辑，如初始化事件ID和热键配置

# 加载热键配置
HotKeyConfig = require(GetPathByRelativePath("config", CURRENT_PATH), "HotKeyConfig", "HotKeyConfig");

# 添加热键配置
_GG("HotKeyManager").addHotKeyConfig(HotKeyConfig);
```