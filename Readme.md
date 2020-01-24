## 基于机器视觉的校园功能房管理系统
### 组成
小程序：用于向用户展示数据  
后端：基于Java的后端数据处理  
采集端：房间的实时图像采集
---
### 小程序
功能列表：
1. 房间信息展示
2. 申请信息填写表单
3. 房间管理员申请信息处理
---

### 后端-数据库
#### 用户信息
1. uid
2. student_wxid
3. student_name 姓名
4. student_college 学院
5. student_id 学号
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

### 审批列表
1. spid
2. approval_sid 申请id
3. approval_rid 审批人
4. approval_result 审批结果  
*0未处理 1通过 2时间段内已使用 3理由不清 4其他原因*
5. approval_time 审批时间
---
