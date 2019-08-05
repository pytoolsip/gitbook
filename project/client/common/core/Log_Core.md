# 日志机制

## 机制实现
  * 基于logging模块进行再次封装，增加d(debug)、i(info)、w(warning)、e(error)接口。
  * 更新输出的消息格式，其中输出的文件路径改为相对工程路径，打印函数允许传入长度可变的参数。

## 使用方式
```py
from _Global import _GG; # 引入全局包

_GG("Log").d("Just Test, ", 233, {"key" : "value"})
# 相当于
_GG("Log").debug("Just Test, ", 233, {"key" : "value"})
```