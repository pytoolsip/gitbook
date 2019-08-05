# 安装组件

## 1. 安装Python包/模块（InstallPythonPackageBehavior）
  * 导出接口  
```py
# 获取已通过pip安装的包
# @params pythonPath python程序路径【不传默认使用环境变量的python】
# @return dict 已安装模块数据
getInstalledPackagesByPip(pythonPath = None);

# 根据pip安装模块
# @params packageName 包/模块名
# @params pythonPath python程序路径【不传默认使用环境变量的python】
# @return bool 是否安装成功
installPackageByPip(packageName, pythonPath = None);

# 更新pip版本
# @params pythonPath python程序路径【不传默认使用环境变量的python】
# @return bool 是否更新成功
updatePipVersion(pythonPath = None);

# 检测模块是否已安装
# @params packageName 包/模块名
# @params pythonPath python程序路径【不传默认使用环境变量的python】
# @return bool 是否已安装
checkPackageIsInstalled(packageName, pythonPath = None);

# 根据pip卸载模块
# @params packageName 包/模块名
# @params pythonPath python程序路径【不传默认使用环境变量的python】
# @return bool 是否卸载成功
installPackageByPip(packageName, pythonPath = None);
```