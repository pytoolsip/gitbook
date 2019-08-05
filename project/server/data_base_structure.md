# 数据库结构

----
## 1. collection表
  * id：收藏唯一ID
  * uid：玩家ID【外键至user的id】
  * tkey：工具键值【外键至tool的tkey】

## 2. comment表
  * id：评论唯一ID
  * uid：玩家ID【外键至user的id】
  * tkey：工具键值【外键至tool的tkey】
  * score：评分
  * content：评论内容【限制在280字符以内】
  * time：评论时间

## 3. exe表
  * id：唯一ID
  * name：名称
  * version：版本号
  * file_path：文件路径
  * changelog：更新日志
  * time：更新时间

## 4. ptip表
  * id：ptip唯一ID
  * version：版本号（3位版本号）
  * file_path：文件路径
  * changelog：更新日志
  * time：更新时间
  * download：下载次数
  * base_version：基础版本号（一般是前2位）
  * update_version：更新版本（一般为base_version，但存在强制更新大版本的情况）

## 5. tool表
  * id：工具唯一ID
  * uid：开发玩家的ID【外键至user的id】
  * tkey：工具键值
  * category：工具分类
  * name：工具名称
  * description：工具描述【限制在255字符以内】
  * score：工具平均评分
  * download：工具下载数
  * time：工具上传时间

## 6. tool_detail表
  * id：唯一ID
  * tkey：工具键值【外键至tool的tkey】
  * version：版本号
  * ip_base_version：依赖平台的基础版本
  * changelog：更新日志
  * file_path：文件路径
  * time：更新时间

## 7. user表
  * id：玩家唯一ID
  * name：玩家名
  * password：登录密码
  * email：绑定邮箱
  * authority：权限（普通用户|管理用户）