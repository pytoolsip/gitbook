# 定时器管理器

----
## 意义
  * 为了统一定时器的管理，避免销毁对象时，定时器仍在运行而导致的出错问题。

## 使用方式
```py
from _Global import _GG; # 引入全局包

# 创建定时器
# Args:
#     parent : 定时器的父类
#     tid : 定时器id
#     callback : 定时器回调
# Returns:
#     timer : 定时器对象
timer = _GG("TimerManager").createTimer(parent, tid = -1, callback = None);


# 销毁定时器
# 【注意要在销毁定时器的父类对象时候，销毁其所创建的所有定时器！】
# Args:
#     timer : 定时器对象
_GG("TimerManager").deleteTimer(timer);
```