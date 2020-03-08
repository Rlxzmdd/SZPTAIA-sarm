## Todo List:
1. 3.15 完成前后端基本结构构思
2. 3.25 完成基本逻辑、界面代码
3. 4.10 完成逻辑、界面优化
## 基于机器视觉的校园功能房管理系统
#### 简介
该项目将用于校园功能房/教室的借用、审批、监控等管理方面。  
#### 组成
小程序：用于向用户展示数据  
后端：基于Java或其他的后端数据处理  
采集端：基于机器视觉的房间实时图像采集
---
### 功能列表
#### 小程序
功能列表：
1. 房间信息展示
2. 申请信息填写表单
3. 房间管理员申请信息处理
#### 后端
1. 用户信息
2. 房间信息
3. 管理员权限
4. 房间申请信息
5. 房间申请信息审批处理
#### 采集端
1. 采集图像
2. 实时检测房间内人数
3. 实时上传至后端
---
### 后端-数据库
#### 用户信息
1. uid
2. student_wxid
3. student_name 姓名
4. student_college 学院
5. student_number 学号
6. student_class 班级
#### 房间信息
1. rid
2. room_name 房间名称
3. room_position 房间位置
4. room_info 房间简介
#### 管理员信息
1. pid
2. op_uid
3. op_power  
*0 为小程序管理员*  
*1 为房间管理员*
4. op_rid  
*所管理的房间rid*
#### 房间人数信息
*由采集端提供*
1. crid
2. collect_rid 房间id
3. collect_number 房间人数
4. collect_time 采集时间
#### 申请列表
1. sid
2. apply_uid 申请用户
3. apply_rid 申请房间
4. apply_reason 申请原因
4. apply_time_start 开始时间
5. apply_time_end 结束时间
6. apply_time_post 申请提交时间
#### 审批列表
1. spid
2. approval_sid 申请id
3. approval_rid 审批人
4. approval_result 审批结果  
*0未处理 1通过 2时间段内已使用 3理由不清 4其他原因*
5. approval_time 审批时间
---
## 开发文档-后端
### 用户相关
1. `POST` /user/add 添加用户   
参数：wx_id 微信用户ID，name 姓名，college 学院，number 学号，class 班级  
2. `GET` /user/select 查询用户信息  
参数：wx_id 微信用户id    
返回：name,college,number  
3. `POST` /user/update 更新用户信息  
....
4. `POST` /user/op/add 添加管理员  
uid 用户ID，power 管理员权限，rid 管理房间  
...
### 房间相关
1. `POST` /room/add 添加房间
2. `GET` /room/selectAll 查询所有房间信息
3. `GET` /room/select 查询房间信息  
参数：rid 房间id
放回：name 名称，position 位置，info 简介
4. ...
### 申请相关
1. `POST` /apply/add  提交一份借用申请  
参数：uid，rid，reason，time_start，time_end
2. `GET` /apply/selectInfoByRid  根据房间id查询目前未处理的借用信息
参数：rid
