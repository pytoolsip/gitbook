# 配置解析组件

## 1. ini配置解析（IniConfigParseBehavior）
  * 导出接口  
```py
# 读取ini配置文件
# @params iniFilePath 文件路径
# @params section ini配置的section
# @params option ini配置的option
# @return string 返回值
readIniConfig(iniFilePath, section, option);

# 写入ini配置文件
# @params iniFilePath 文件路径
# @params section ini配置的section
# @params option ini配置的option
# @params value ini配置对应section和option的值
writeIniConfig(iniFilePath, section, option, value);

# 移除ini配置文件
# @params iniFilePath 文件路径
# @params section ini配置的section
# @params option ini配置的option【可选】
removeIniConfig(iniFilePath, section, option = None);
```

## 2. json配置解析（JsonConfigBehavior）
  * 导出接口  
```py
# 写入json配置文件
# @params filePath 文件路径
# @params data json数据
writeJsonFile(filePath, data)

# 读取json配置文件
# @params filePath 文件路径
# @return data json数据
readJsonFile(filePath)
```

## 3. xml配置解析（XmlConfigParseBehavior）
  * 导出接口  
```py
# 根据文件路径，获取元素树对象
# @params filePath 文件路径
# @params xml元素树对象
getElementTreesByFilePath(filePath)
```