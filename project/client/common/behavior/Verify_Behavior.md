# 校验组件

## 校验环境
  * 导出接口  
```py
# 校验python环境
# @params pythonPath python程序路径【不传默认使用环境变量的python】
# @return bool 是否校验通过
verifyPythonEnvironment(pythonPath = None);

# 校验python版本
# @params fVer 首位版本号
# @params sVer 次位版本号
# @params pythonPath python程序路径【不传默认使用环境变量的python】
# @return bool 是否校验通过
verifyPythonVersion(fVer = 3, sVer = 4, pythonPath = None);

# 校验pip环境
# @params pythonPath python程序路径【不传默认使用环境变量的python】
# @return bool 是否校验通过
verifyPipEnvironment(pythonPath = None);
```