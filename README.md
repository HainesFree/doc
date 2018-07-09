# 持悦服务器数据结构设计

版本 | 日期 | 作者 | 修改内容
-------------------- | -------------------- | -------------------- | --------------------
V3.0.0 | 2017-10-19 | Jacky | 初始3.0文档
V3.0.1 | 2017-10-31 | Jacky | 新增表 clt_customer_refer_records
V3.0.2 | 2017-11-06 | luogc | 新增表 clt_customer_packs、clt_customer_contents、clt_customer_recharge_orders、clt_customer_gold_coin_records、clt_customer_consume_records、clt_customer_coupons、clt_customer_invitations、clt_customer_openid_token	修改表： clt_customer_accounts、clt_client_customers
V3.0.3 | 2017-11-08 | panzhen | 修改表 cnt_packs
V3.0.3 | 2017-10-31 | Jacky | 修改表 clt_client_contents clt_client_packs 字段定义, 增加 表 ntc_notification_records 字段
V3.1.0 | 2017-10-31 | Jacky | 增加 表 cnt_pack, clt_customer_share_images, agt_agent_port_operations,agt_agents,clt_customer_details,clt_customer_register_orders 字段 新增表 clt_client_accelerate_orders ， clt_client_accelerate_records
v3.2.0 | 2017-12 |luo |修改表 cnt_achievements
v3.2.0 | 2017-12 |panzhen |增加表 cnt_content_relations
v3.2.0 | 2017-12 |panzhen |修改表 cnt_contents
v3.2.0 | 2017-12 |Jacky |修改表 clt_customer_coupons， clt_customer_gold_coin_records 字段定义
v3.2.0 | 2017-13 |Jacky |增加表 clt_customer_comment_blocks
v3.2.0 | 2017-13 |luo |增加表 clt_customer_share_records、clt_learning_poinFt_ranking_monthly、clt_department_ranking_monthly、clt_learning_point_ranking_monthly_likes、clt_department_ranking_monthly_likes、plt_platform_customer_lock_records
v3.2.0 | 2017-25 |Jacky | 增加表 agt_cooperators, agt_agent_cooperators, agt_cooperator_packs, agt_cooperator_share_images
v3.2.0 | 2017-25 |Jacky | 修改表 cnt_packs
v3.2.0 | 2017-25 |Jacky | 增加表 agt_cooperator_shared_daily_records, agt_cooperator_shared_checks, agt_cooperator_shared_check_handler_records
v3.2.0 | 2017-26 |Jacky | 增加表 agt_cooperator_devices
v3.2.0 | 2017-26 |luo |增加表 plt_redeem_codes、agt_agent_redeem_code_batchs、agt_agent_redeem_code_dispatch_check_records、agt_agent_redeem_code_transfer_check_records、agt_agent_redeem_code_transfer_records、agt_agent_redeem_code_dispatch_records、clt_customer_redeem_code_records
v3.2.0 | 2017-28 |Jacky | 修改表 cnt_packs, clt_customer_packs, clt_client_packs
v3.2.0 | 2018-01-01 |Jacky | 增加表 agt_cooperator_share_customers
v3.2.0 | 2018-01-03 |Jacky | 修改表 agt_agents 增加表 agt_agent_details
v3.2.0 | 2018-01-03 | qiuxn | agt_cooperator_pack_monthly_settlements、agt_cooperator_customer_register_monthly_settlements、agt_cooperator_customer_recharge_monthly_settlements、agt_cooperator_monthly_settlement、agt_cooperator_quarter_issues
v3.2.0 | 2018-01-04 |Jacky | 修改表 clt_client_packs, agt_agent_addresses
v3.2.0 | 2018-01-04 | qiuxn | 修改表 clt_customer_packs
v3.2.0 | 2018-01-05 | qiuxn | 修改表 clt_customer_contents
v3.2.0 | 2018-01-12 | Jacky | 修改表 clt_customer_content_comments
v3.2.0 | 2018-01-12 | Jacky | 修改表 clt_customer_content_comment_reviews
v3.2.0 | 2018-01-12 | Jacky | 修改表 clt_customer_content_comment_likes
v3.2.0 | 2018-01-12 | Jacky | 修改表 clt_customer_content_comment_rewards
v3.2.0 | 2018-01-12 | Jacky | 修改表 clt_customer_content_comment_messages
v3.2.0 | 2018-01-12 | Jacky | 修改表 clt_customer_feedback
v3.2.0 | 2018-01-12 | qiuxn | 增加表 agt_port_allocate_records, agt_port_allocate_orders
v3.3.0 | 2018-01-25 | wangb | 修改表 app_slides
v3.3.0 | 2018-01-25 | panzz | 增加表 clt_customer_agents
v3.3.0 | 2018-01-25 | Jacky | 增加表 app_slide_records
v3.3.0 | 2018-01-26 | Jacky | 增加表 agt_cooperator_details
v3.3.0 | 2018-01-26 | panzz | 修改表 agt_port_allocate_records, agt_port_allocate_orders
v3.3.0 | 2018-01-30 | wangb | 修改表 rpt_client_records


## 数据库表设计说明
* ID 值使用无符号，int 类型
* 所有字符型默认值为 “”
* 所有数值型默认值为 0


# Domain platform
##  plt_platform_users

总部平台用户

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
user_name | varchar(50) | | | 账户名
user_pass | varchar(100) | | | 账户密码
real_name | varchar(50) | | | 真实姓名
last_login | timestamp | | | 最后登录时间
active | tinyint(1) | | | 记录删除标识

说明：
* 密码使用Shiro 自带 SHA256 不可逆加密


## plt_platform_roles

总部平台角色

字段 | 类型 | Extra | 默认 | 备注
----------| ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
role_name | varchar(50) | | | 角色名
active | tinyint(1) | |0 | 记录删除标识

说明：


## plt_platform_user_roles

总部平台用户角色

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
role_id | int(11) |unsigned | | 角色ID
user_id | int(11) |unsigned | | 用户ID
active | tinyint(1) | | 0| 记录删除标识

说明：


## plt_platform_permissions

总部平台权限

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
permission_name | varchar(50) | | | 权限名称
active | tinyint(1) | | 0| 记录删除标识

说明：


## plt_platform_role_permissions

总部平台角色权限

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
permission_id | int(11) |unsigned | | 权限ID
role_id | int(11) | unsigned| | 角色ID
active | tinyint(1) | |0 | 记录删除标识

说明：


## plt_platform_menus

总部平台菜单链接

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11)       | unsigned | auto_increment | 自增ID
menu_name    | varchar(100)   | | | 菜单名
menu_link    | varchar(500)  | | | 菜单链接
menu_rank    | int(11)   | unsigned | | 菜单顺序
menu_level   | int(11)   | unsigned | | 菜单级别
parent_menu_id | int(11)|unsigned| | 父菜单ID
active       | tinyint(1) | | 0| 记录删除标识

说明：


## plt_platform_permission_menus

总部平台权限对应链接

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
permission_id | int(11) |unsigned | | 权限ID
menu_id | int(11) | unsigned| | 菜单ID
active | tinyint(1) | |0 | 记录删除标识

说明：


## plt_apks

apk版本库

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
apk_name | varchar(50) || | apk 名称
download_url |varchar(255)| | | apk URL
version_name |varchar(50)| | | APP版本号
version_desc | text | | | 版本信息
version_size | varchar(100) | | | APP大小
app_version | int(11) | unsigned| | APP数字版本号
is_force | tinyint(1) | |0 | 是否强制升级
apk_hashcode | varchar(50) | | | 文件hash码
created_at | timestamp || | 创建日期
updated_at | timestamp | | | 更新日期
active | tinyint(1) | |0 | 记录删除标识

is_force 是否强制升级： 1 是 0 否


## plt_platform_agent_lock_records

持悦平台操作用户锁定/解锁代理商记录表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
platform_user_id | int(11) |unsigned | | 平台用户ID
agent_id | int(11) | unsigned| | 代理商ID
event_type | tinyint(1) | unsigned|1 | 事件类型
created_at | timestamp | | | 创建日期

event_type 为锁定或解锁类型，1 ： 为锁定事件  2：解锁事件


## plt_messages

运营后台公告

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
message_title | varchar(255) | | | 公告标题
tag_id |int(11)| | | 标签ID
tag_title |varchar(200)| | | 标签名称
message_file | varchar(255) | | | 公告文件URL
message_video | varchar(255) | | | 公告视频
message_body | text | | | 公告详情
message_type | tinyint(1) | | | 公告类型
is_published | tinyint(1) || | 是否发布
created_by | int(11) | unsigned| | 创建人
updated_by | int(11) | unsigned| | 更新人
created_at | timestamp | | | 创建日期
updated_at | timestamp | | | 修改日期

message_type 公告类型
1： 代理商公告
is_published 是否发布
1： 未发布 0：已发布 2 :发布中


## plt_message_tags

运营公告标签

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
tag_title | varchar(200) | | | 标签名称


## plt_backup_queue_messages

消费失败的消息列表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
message_type | varchar(200) | | | 消息类型
message_body | text | | | 消息体
created_at | timestamp | | | 创建日期
active | tinyint(1) | | | 删除标识


## plt_recharge_configuration

充值配置

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
recharge_type | tinyint(1) | | | 价格类型
recharge_size | bigint(11) | | | 容量/流量大小
recharge_cost | bigint(11) | | | 充值金额
recharge_discount | int(11) | | | 折扣比例 1-99
recharge_unit_cost | bigint(11) | | | 单价

recharge_type 价格类型
1：为存储容量 2：为流量


## plt_splash_images

开屏图片，每年的所有节气，对应的图片

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
festival_year | char(4) | | | 年份
festival_date | datetime | | | 节日/节气日期
festival_title | varchar(50) | | | 节日/节气名称
splash_image | varchar(200) | | | 对应的开屏图片
agent_sale_clue_image | varchar(255) | | | 代理商销售线索分享图
active | tinyint(1) | | | 删除标识



## plt_customer_welcome_pages

欢迎页管理表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
body | text | | | 欢迎页内容体
url | varchar(255) | | | 欢迎页H5地址
account_type | tinyint(1) |unsigned | | 版本类型
status| tinyint(1) |unsigned | | 欢迎页面状态

account_type：

- 0.企业标准版用户 
- 1.企业体验版用户 
- 2.社群体验版用户 
- 3.社群标准版用户 
- 4.企业pro版用户 
- 5.社群尊享版用户

status 欢迎页面状态：

- 1:启用
- 2:禁用

## plt_platform_customer_lock_records

用户锁定记录表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
platform_user_id| int(11) | unsigned |  | 操作人ID
client_customer_id| int(11) | unsigned |  | 用户客户id
event_type| tinyint(11) | unsigned |  | 事件类型
created_at| timestamp | | | 创建时间


<font color="red">
## plt_redeem_codes

用户锁定记录表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
batch_id| int(11) | unsigned |  | 批次id
redeem_code_number| varchar(50) |  |  | 兑换码流水号
redeem_code_title| varchar(100) |  |  | 兑换码
batch_level_one_id| int(11) |  |  | 白金代理商
batch_level_two_id| int(11) |  |  | 金代理商
batch_level_three_id| int(11) |  |  | 银铜代理商
agent_id| int(11) |  |  | 当前拥有代理商
item_type| tinyint(1) |  |  | 1：精英会员；2：定向课程卷；3：课程卷数量；金币数量
item_content| varchar(500) |  |  | 1，3，4：为数值   2：以|分割的课程id
redeem_code_status| tinyint(1) |  |  | 0：未使用  1：已使用  2：已过期
enable_status| tinyint(1) |  |  | 0：未启用  1：已启用
expired_time| timestamp | | | 过期时间
</font>

## app_slides

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
slide_image | varchar(255) |  | | 图片url
slide_action| varchar(7) |  | | action类型
action_id | int(11)| unsigned | 0 | action ID
content_type | tinyint(1) |  | 1 | 若是跳转至内容，需要设置视频或者音频
rank| int(11) | unsigned | 0 | 序号
active | int(11)|  | 0 | 删除标识
<font color="red">slide_type</font> | tinyint(1) | | | 轮播图位置类型
<font color="red">is_published</font> | tinyint(1) | | | 轮播图状态
<font color="red">slide_description</font> | varchar(200) | | | 一句话介绍
<font color="red">created_at</font> | timestamp | | | 创建时间
<font color="red">slide_title</font> | varchar(200) | | | 课程名称


slide_action定义

- APP_CNT : 跳转至内容动作，action id 为content id
- APP_PCK : 跳转到课程列表页，action id 为 pack id

content_type定义内容类型： 

- 1 为视频 
- 2 为音频

slide_type 

- 0 app首页
- 1 课程页

is_published
- 0 已启用
- 1 未启用
- 2 禁用

<font color="red">

## app_slide_records

轮播图点击记录表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
slide_id  | int(11)  | unsigned |  | 轮播图图片ID
client_customer_id | int(11) | unsigned |  | 企业用户关系ID
customer_id  | int(11)  | unsigned |  | 用户ID
customer_type | tinyint(1) | unsigned |  | 注册用户类别
client_id | int(11) | unsigned | | 用户所属客户ID
created_at | timestamp |  |  | 创建时间

</font>



## app_tags

App 的标签导航，此处有冗余信息

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
tag_id | int(11) | unsigned | | tag ID
tag_title| varchar(50) |  | | tag 标题
tag_icon | varchar(200) |  |  | tag 图片
display_type | tinyint(1) |  | | 点击Tag后显示类型
rank| int(11) | unsigned |  | 序号

display_type 点击Tag后显示类型
1 : 简单列表 2 : 分组列表



# Domain DIC

## dic_provinces

省份字典

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
province_code | char(4) |  | | 省份Code
province_name | varchar(50) |  | | 省份名称
short_name | varchar(10) |  |  | 英文缩写
active | tinyint(1) |  |  | 删除标识



## dic_cities

城市

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
province_code | char(4) |  | | 省份Code
city_code | char(4) |  | | 城市code
city_name | varchar(50) |  | | 城市名称
short_name | varchar(10) |  |  | 英文缩写
active | tinyint(1) |  |  | 删除标识



## dic_counties

区/县表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
province_code | char(4) |  | | 省份Code
city_code | char(4) |  | | 城市code
county_code | char(4) |  | | 区县code
county_name | varchar(50) |  | | 区县名称
short_name | varchar(10) |  |  | 英文缩写
active | tinyint(1) |  |  | 删除标识


## dic_authors

作者字典库

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
author_code | char(3) |  | | 作者code
author_name | varchar(200) |  | | 作者名称
active | tinyint(1) |  |  | 删除标识


## dic_publishers

出版社字典库

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
publisher_code | char(3) |  | | 出版社code
publisher_name | varchar(200) |  | | 出版社名称
active | tinyint(1) |  |  | 删除标识


## dic_configurations

全部配置表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
config_key | varchar(100) |  | | 配置项key
config_value | varchar(100) |  | | 配置项value
config_description | varchar(512) |  |  | 配置说明
created_at | timestamp |  |  | 创建时间


# Domain Content
## cnt_packs

内容课程包数据结构

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
<font color="red">pack_type</font> | tinyint(1) | | | 课程类型
pack_title | varchar(100) | | | 课程包标题
pack_cover | varchar(255) | | | 课程包封面
pack_image | varchar(255) | | | 课程介绍图
pack_preview_image| varchar(255) | | | 课程预告图
pack_speaker | varchar(50) | | | 主讲人
speaker_title | varchar(255) | | | 主讲人头衔
pack_summary | varchar(200) | | | 课程包说明
pack_description | text | | | 课程内容简介
pack_description_html | varchar(200) | | | 课程内容简介html
generate_status| tinyint | | | 是否生成
pack_amount | int(11) | | | 课程含有课时的数量
pack_price | int(11) | | | 课程金币价格
trial_video_url | varchar(255) | | | 试看视频地址
trial_video_duration | int(11) | | | 试看视频时长
trial_audio_url | varchar(255) | | | 试听音频地址
trial_audio_duration | int(11) | | | 试听音频时长
is_trial| tinyint | | | 是否体验
is_published| tinyint(1) | | | 课程包是否已经发布
publish_time | timestamp | | | 平台发布时间
customer_share_bg | varchar(255) | | | 课程邀请分享图背景
<font color="red">cooperator_id</font> | int(11) | un | | 关联的老师ID
<font color="red">enable_enterprise</font> | tinyint(1) | | | 企业版显示状态
<font color="red">enable_community</font> | tinyint(1) | | | 社群版显示状态
created_at | timestamp | | | 创建时间
updated_at| timestamp | | | 修改时间
active | tinyint(1) | | | 删除标识

is_published 是否已经被发布

- 0:已发布
- 1：未发布/撤回
- 2: 发布中

is_trial  
- 0: 不允许体验  
- 1: 允许体验

<font color="red">
pack_type 课程类型

- 0 : 必修课
- 1 : 选修课

generate_status

- 1:待生成;
- 0:已生成;
- 2:生成中

enable_enterprise， enable_community

- 0 : 不显示
- 1 : 显示  

</font>

## cnt_tags

内容标签

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
tag_title | varchar(50) | | | 标签标题
tag_icon | varchar(200) | | | 标签icon


## cnt_content_tags

内容与tag 关系

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
content_id | int(11) |unsigned | | 内容ID
tag_id | int(11) | unsigned| | 标签 ID


## cnt_contents

内容数据结构，此处有冗余数据

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
content_class | tinyint(1) | |0 | 0：普通内容1：课程内容
pack_id | int(11)|unsigned | 0| 课程包ID
content_title | varchar(200) | | | 内容标题
content_cover| varchar(255) | | | 内容图片
content_cover_gray | varchar(255) | | | 内容灰度图片
player_cover | varchar(255) | | | 内容播放器图片
content_image | varchar(255) | | | 内容详情页顶部图片
content_preview_image | varchar(255) | | | 内容预告图片
summary| varchar(500) | | | 一句话说明
publish_date | date | | | 发布日期
publish_rank | int(11) | | | 发布日期
video_url| varchar(255) | | | 视频地址
video_duration | int(11) | | | 视频时长
audio_url | varchar(255) | | | 音频地址
audio_duration | int(11) | | | 音频时长
trial_video_url | varchar(255)| | | 试看视频地址
trial_video_duration | int(11)| | | 试看视频时长
trial_audio_url| varchar(255)| | | 试听音频地址
trial_audio_duration | int(11)| | | 试听音频时长
content_txt | text | | | 文本内容
essential_content | text | | | 精华解读
enable_essential | tinyint(1) | | 0| 是否启用精华解读
essential_content_html | varchar(255) | | | 精华解读页面URL
essential_breviary_title | varchar(255) | | | 精华解读摘要title
essential_breviary_description | varchar(255) | | | 精华解读摘要描述
essential_breviary_image | varchar(255) | | | 精华解读摘要图片
essential_breviary_content | text | | | 精华解读摘要内容
essential_breviary_html | varchar(255) | | | 精华解读摘要页面URL
author_code| char(3) | | | 作者code
author_name | varchar(20) | | | 作者名称
isbn | varchar(50) | | | ISBN
publisher_code | char(3) | | | 出版社code
publisher_name | varchar(50) | | | 出版社名称
desc_title | varchar(200) | | | 详细介绍标题
description| text | | | 详细介绍
assignment_id_list | text | | | 关联的作业本id列表
content_html| varchar(255) | | | 内容详情的网页地址
content_size| bigint(11) | | | 内容容量KB
content_price| int(11) | | | 内容金币价格
is_trial| tinyint | | | 是否体验
is_published | tinyint(1) | | 1| 是否已经被发布
publish_tag | tinyint(1) | | 0| 发布标签
created_at| timestamp | | | 创建时间
updated_at | timestamp | | | 修改时间
active | tinyint(1) | | | 删除标识

is_published 是否已经被发布

- 0: 已发布
- 1: 未发布/撤回
- 2: 发布中

内容类型：

- 0：普通内容
- 1：课程内容

publish_tag 课程内容的发布标签，只有在内容属于课程时才起作用
标签为常量，1，2，3，4，分别表示每月第一周发布，每月第二周发布。。。以此类推

is_trial

- 0:不允许体验  
- 1:允许体验

<font color="red">
enable_essential  

- 0 禁用  
- 1 启用

</font>


## cnt_content_queques

平台内容发布队列

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
content_id | int(11) |unsigned | | 内容ID
publish_rank | int(1) | unsigned| | 发布序号
is_top | tiny(1) | | | 是否置顶

is_top: 

- 1 置顶
- 0 非置顶

置顶内容会修改客户的内容队列


## cnt_pack_queques

平台内容发布队列

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
pack_id | int(11) |unsigned | | 内容ID
publish_rank | int(1) | unsigned| | 发布序号
is_top | tiny(1) | | | 是否置顶

is_top:
 
- 1 置顶
- 0 非置顶

置顶内容会修改客户的课程包队列

<font color="red">

## cnt_content_relations

书籍关联

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
content_id | int(11)|  |  | 内容ID
relative_content_id | int(11) |  | | 关联内容ID
content_type | tinyint(1)  |  |  | 内容类型
relative_content_title | varchar(255) |  | | 关联内容title
relative_content_cover | varchar(255) |  | | 关联内容图片
created_at | timestamp |  | | 创建日期

</font>



## cnt_content_html_records

内容生成HTML记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned |  | 自增ID
content_id | int(11) | unsigned | 0 | 内容ID
<font color="red">html_type</font> | tinyint(1) |unsigned |0 | 文件类型
generate_type | tinyint(1) |unsigned |0 | 生成类型
is_finished | tiny(1) | | 0| 是否生成完成
operate_by | int(1) | | 0| 操作人
start_time | timestamp | | | 生成开始时间
end_time | timestamp | | | 生成完毕时间

is_finished 生成状态
- 1： 待生成
- 0：已生成
- 2 :生成中

generate_type 生成类型。
- 0： 全部生成
- 1：单个生成

<font color="red">
html_type 文件类型

- 1 : 描述内容
- 2 : 精华解读

</font>

## cnt_assignments

作业本

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | un | auto_increment | 自增ID
assignment_title | varchar(100) |  |  | 作业本标题
assignment_image | varchar(255) | | | 作业本图片
quiz_total | int(11) |un | | 题目数量
assignment_time | int(11) |un | | 做题时间（单位分钟）
content_id_list | text | | | 关联的内容ID列表
pack_id_list | text | | | 关联的课程的课时ID列表
is_published | tinyint(1) | | | 发布状态
active | tinyint(1) | | | 删除标识

is_published 是否已经被发布 0:已发布 1：未发布/撤回 2: 发布中


## cnt_assignment_quizs

作业题目

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
assignment_id | int(11) | unsigned |  | 所属作业ID
quiz_rank | int(11) |unsigned | | 问题序号
quiz_title |varchar(255) | | | 问题标题
quiz_answers | varchar(200) | | | 答案列表
quiz_type | tinyint(1) | | | 题目类型
active | tinyint(1) | | | 删除标识

quiz_type 题目类型， 1：单选 2：多选


## cnt_assignment_quiz_results

作业答案列表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
quiz_id | int(11) | unsigned |  | 作业问题ID
result_title |varchar(255) | | | 答案标题
result_rank | int(11) | | | 答案序号
active | tinyint(1) | | | 删除标识


## cnt_medal_categories

勋章类型

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
category_title | varchar(50) |  |  | 类型标题
assignment_ids |varchar(255) | | | 必须完成的作业本ID列表,以|隔开
category_sharebg | varchar(500) | | | 勋章类型分享图片背景
active | tinyint(1) | | | 删除标识


## cnt_medals

勋章

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
category_id | int(11) |  |  | 勋章类型ID
medal_grade |tinyint(1) | | | 1,2,3
medal_title | varchar(100) | | | 勋章标题
medal_image_on |varchar(255) | | | 勋章可用图片
medal_image_off | varchar(255) | | | 勋章不可用图片
assignment_amount | int(11) | | | 必须完成的作业本数量
active | tinyint(1) | | | 删除标识

## cnt_pack_tags
课程标签关联

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
pack_id | int(11) | unsigned | 0 | 课程id
tag_id  | int(11) | unsigned | 0 | 标签id


## cnt_achievement_categories

成就类型

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
category_title  | varchar(50) |  | | 类型标题
status | tinyint(1) |  |  | 类型状态
active  | tinyint(1) |  |  | 删除标识

status  1:启用   0：禁用


## cnt_achievements

成就

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
category_id | int(11) |  |  | 类型id
achievement_title | varchar(50) | | | 成就名称
summary | varchar(255) | | | 成就简介
condition_summary | varchar(255) | | | 获取条件说明
category_title | varchar(50) | | | 类型标题
achievement_image_on | varchar(255) | | | 成就获取的图片
achievement_image_off | varchar(255) | | | 成就未获取的图片
display_off | tinyint(1) | | | 成就是否启用
<font color="red">achievement_type</font>  |  tinyint(1) |   |   |  成就类型
status |tinyint(1) | | | 上架下架
achievement_sharebg | varchar(255) | | | 成就分享背景图
created_at |timestamp | | | 创建时间
created_by | int(11) | | | 创建者id
updated_at | timestamp | | | 更新时间
updated_by | int(11) | | | 更新者id
active  | tinyint(1) |  |  | 删除标识

display_off  0:未启用   1：启用
status  0：下架，  1：上架
achievement_type  0 通用  1 社群版非会员  2 社群版精英  3企业同步版  4企业异步版

## cnt_achievement_rule_classes

成就规则类型

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
class_title  | varchar(255) |  | | 规则类型标题
event_type | int(11) |  |  | 事件类型
achievement_ids  | varchar(500) |  |  | 成就ID

event_type  1:学习时长  2:学习天数  3:学习力 4:分享次数


## cnt_achievement_rules

成就规则

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto_increment | 自增ID
achievement_id | int(11) |  |  | 成就id
rule_class_id | int(11) | | | 规则类型id
summary_type | tinyint | | | 统计类型
condition_type | tinyint | | | 条件类型
operate_type | tinyint | | | 操作符类别
operate_number | varchar(255) | | | 数值
unit_type | tinyint(1) | | | 单位
rule_rank |int(11) | | |规则排序号
rule_operate_type | tinyint(1) | | | 规则操作符类别
created_by | int(11) | | | 规则创建者
update_time | timestamp | | | 更新时间
update_by | int(11) | | | 更新者
created_at |timestamp | | | 创建时间
active  | tinyint(1) |  |  | 规则删除标记

operate_type  1: 大于   2：大于等于  3：小于  4：小于等于  5：等于
rule_operate_type 0:没有操作符  1: and
summary_type: 1: 总  2：每日   3：连续
contidtion_type: 0:数值 1：时间
unit_type:  0：数值   1：分钟 2：小时 3：天 4：周  5：月  6：特定时间

# Domain Agent
## agt_agents

代理商信息

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
grade_code | char(1) | | | 代理商等级
grade_title | varchar(20) | | | 代理商等级名称
trail_client_limitation | int(11)| un | | 体验用户限制
trail_client_limitation_extra| int(11) | un | | 自定义体验用户
agent_number | varchar(20) | | | 代理商编号
agent_name | varchar(50) | | | 代理商账户
agent_pass | varchar(100) | | | 代理商密码
province_code| char(3) | | | 省code
province_name | varchar(50) | | | 省会名称
city_code | char(3) | | | 城市code
city_name| varchar(50) | | | 城市名称
agent_title | varchar(50) | | | 代理名称
contact_name | varchar(50) | | | 联系人姓名
contact_mobile | varchar(50) | | | 联系手机
port_stock| int(11) | un | | 累计进货端口数
port_stock_plt | int(11) | un | | 累计赠送端口数
port_inventory | int(11) | un | |端口库存数量
port_inventory_plt | int(11) | un | | 端口平台赠送库存
port_inventory_portpoint | int(11) | un | | 剩余端口点数
clue_qrcode| varchar(200) | | | 销售线索二维码
refer_qrcode | varchar(200) | | | 社群版推荐二维码
refer_qrcode_share | varchar(255) | | | 社群版推荐二维码带背景
agent_type | tinyint(1) | | | 代理商类型
last_login| timestamp | | | 最后登录时间
agent_status | tinyint(1) | | | 代理状态
level_one_id | int(11) | | | 一级代理ID
parent_id | int(11) | | | 父ID
relative_depth | tinyint(1) | | | 关系深度
storage_used_total | bigint(11) | | | 代理商客户容量使用总数
bandwidth_used_total | bigint(11) | | | 代理商客户流量使用总数
enable_transfer| tinyint(1) | | | 是否开启端口转移功能
contract_url | varchar(200) | | | 代理商合同URL
contract_subject | tinyint(1) | | | 签约主体
contract_name | varchar(200) | | | 签约名称
first_boot_web | tinyint(1) | | | 第一次登陆标识
created_by | int(11) | un | | 创建管理员ID
created_at| timestamp | | | 创建时间
active | tinyint(1) | | | 删除标识

grade_code 代理商等级
端口点数说明，1个端口等于365个端口点数
agent_status 代理商账户状态

- 0 ： 正常
- 1 ：被锁定

enable_transfer 是否开启端口转移功能

- 1： 开启
- 0： 关闭

agent_type 代理商类型

- 0：普通代理商
- 1：社群版代理商

first_boot_web

- 0: 完成登陆事件
- 1: 需填写发票信息
- 2: 需填写银行信息
- 3: 两项都需填写

contract_subject

- 1: 企业
- 2: 个人

<font color="red">

## agt_agent_details

代理商详情，主要记录发票及银行信息

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
agent_id | int(11) | un | | 代理商ID
invoice_title | varchar(255) | | | 发票抬头
registration_number | varchar(50) | | | 纳税人识别号
invoice_type | tinyint(1) | un | | 发票类型
bank_name | varchar(255) | | | 开户行名称
bank_account | varchar(100) | | | 银行账号
company_address | varchar(255) | | | 公司地址
company_phone | varchar(50) | | | 公司电话
share_bank_name | varchar(255) | | | 社群版分润银行开户行
share_bank_account | varchar(100) | | | 社群版分润银行银行账号
created_at | timestamp | | | 创建日期
updated_at | timestamp | | | 更新日期

invoice_type 发票类型

- 1: 增值税普通发票
- 2: 增值税专用发票

## agt_agent_addresses

代理商地址

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
agent_id   | int(11) | un | | 代理商ID
receiver | varchar(50) |  |  | 收件人
address_detail | varchar(500) |  |  | 详细地址
receiver_phone | varchar(50) |  |  | 联系电话
is_default | tinyint(1) | un | | 是否默认
created_at| timestamp | | | 创建时间
updated_at | timestamp | | | 更新日期
active | tinyint(1) | | | 删除标识

is_default 是否默认

- 0: 默认
- 1: 非默认

</font>

## agt_agent_port_check_records

代理商充端口（及赠送端口）、转移端口记录审核记录表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
record_type | tinyint(1) | un | | 记录类型
platform_user_id| int(11) | un | | 操作平台用户
from_agent_id | int(11)| un | | 被转出端口代理商ID
to_agent_id| int(11) | un | | 被充值端口代理商ID
port_amount | int(11) | un | | 正式端口数
port_amount_plt | int(11) | un | | 赠送端口数
check_platform_user_id | int(11) | | | 平台审核用户ID
check_platform_admin_id| int(11) | | | 平台审核管理员ID
check_status | tinyint(1) | | | 审核状态
status_message | varchar(255) | | | 审核拒绝理由（若不通过）
status_admin_message| varchar(255) | | | 管理员审核拒绝理由
checked_at | timestamp | | | 审核时间
checked_admin_at | timestamp | | | 管理员审核时间
created_at | timestamp | | | 创建日期

record_type 记录类型
1：平台端口充值  2：代理商端口转让
check_status 审核状态
0：平台管理审核通过
1：待平台审核
2：平台拒绝
3：平台通过/待管理员审核
4：平台管理拒绝


## agt_agent_port_check_record_logs

审核日志记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
check_id | int(11) | un | | 审核记录ID
from_check_status| tinyint(1) | un | | 更改前审核状态
to_check_status | tinyint(1)| un | | 更改后审核状态
created_at | timestamp | | | 创建日期



## agt_agent_port_operations

代理商端口操作记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
check_id | int(11) | un | | 对应的审核记录ID
agent_id| int(11) | un | | 代理商ID
level_one_id | int(11)| un | | 根代理商ID
parent_id | int(11) | un | | 父级代理商ID
relative_agent_id | int(11) | un | | 转让/收到端口代理商ID
receive_client_id | int(11) | un | | 分配端口的客户ID
event_type | char(8) |  | | 事件类型
operate_type| char(3) |  | | 端口操作类型
operate_amount | int(11) | un | | 操作端口数量
port_amount | int(11) | un | | 点数对应端口数量
portpoint_amount| int(11) | un | | 每端口点数
operate_by | int(11) | un | | 操作人ID
operate_admin_by | int(11) | un | | 平台管理员ID
created_at | timestamp | | | 创建日期

event_type 事件类型：

- 000 ： 购买
- 001 ： 开户
- 002 ： 赠送
- 003 ： 扩容
- 004 ： 体验用户初始化端口
- 005 ： 转入
- 006 ： 转出
- 007 ： 续费
- 008 ： 加速

operate_type 操作类型：
ADD 增加库存  MIN 减少库存


## agt_agent_client_lock_records

代理商锁定/解锁客户操作记录表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
agent_id | int(11) | un | | 代理ID
client_id| int(11) | un | | 客户ID
event_type | tinyint(1)| un | | 事件类型
created_at | timestamp |  | | 创建日期

event_type 为锁定或解锁类型，1 ： 为锁定事件 2：解锁事件


## agt_agent_messages

代理商公告表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
message_id | int(11) | un | | 平台公告ID
agent_id| int(11) | un | | 代理商ID
message_title | varchar(255)|  | | 公告标题
tag_title | varchar(200)|  | | 公告标签
message_file | varchar(255) |  | | 公告文件URL
message_video | varchar(255) |  | | 公告视频
message_body | text |  | | 公告详情
has_read| tinyint(1) |  | | 是否已阅读
read_time | timestamp |  | | 阅读时间
created_at | timestamp | | | 创建日期
active| tinyint(1) | un | | 删除标识

has_read 是否已阅读
1： 未阅读 0：已阅读


## agt_agent_sale_clues

代理商销售线索

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
agent_id | int(11) | un | | 代理商ID
company_name | varchar(200) |  | | 企业名称
company_scale | varchar(255)|  | | 企业规模
company_location| varchar(200) |  | | 企业所在地
province_code | char(4) |  | | 省份Code
province_name | varchar(50) |  | | 省份名称
city_name | varchar(50) | | | 城市名称
contact_name| varchar(50) | | | 联系人
contact_phone | varchar(50) | | | 联系电话
source_code | tinyint(1) | | | 来源ID
source_title| varchar(50) | | | 来源标题
original_source_title | varchar(50) | | | 原来源标题
clue_status | tinyint(1) | | | 状态
created_at | timestamp | | | 创建日期
updated_at | timestamp|  | | 更新日期
updated_by| int(11) |  | | 更新代理商ID
updated_admin_by | int(11) |  | | 更新后台ID
dispatch_status | tinyint(1)|  | | 是否被分配
dispatched_at | timestamp | | | 被分配时间
dispatched_by| int(11) | | | 分配操作用户
dispatched_by_name | varchar(50) | | | 平台操作用户名
active| tinyint(1) | | | 删除标识

clue_status 状态: 1：未跟进 0：已跟进
dispatch_status 分配状态： 0 已分配 1：未分配


## agt_agent_grades

代理商等级

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
grade_code | char(1) |  | | 等级Code
short_name| char(1)| | | 代理商等级简称
grade_title | varchar(50)|  | | 等级标题
trail_client_limitation | int(11)| un | | 体验用户数量限制
parent_id | int(11) | un | | 父级ID



## agt_agent_association_records

代理商关联记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
former_parent_id | int(11) |  | | 原有父ID
current_parent_id| int(11)|  | | 更改后父ID
operate_by | int(11)|  | | 操作人
created_at | timestamp|  | | 操作时间
active | tinyint(1) |  | | 删除标识


## agt_content_groups

代理商开户书籍组合

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
agent_id | int(11) | un | | 代理商ID
group_title| varchar(200) |  | | 组合名称
is_default | tinyint(1) |  | | 是否默认 1：是 0：否
active | tinyint(1) |  | | 删除标识

is_default是否默认
1：是 0：否



## agt_content_group_items

代理商开户书籍组合的书籍列表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
group_id | int(11) | un | | 组合ID
content_id| int(11) | un | | 内容ID
active | tinyint(1) | un | | 删除标识


## agt_agent_consults

渠道预约咨询

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
consult_name | varchar(50)|  | | 姓名
consult_mobile| varchar(50)|  | | 手机号码
company_name | varchar(200)|  | | 公司名称
company_email | varchar(100)|  | | 邮箱
created_at | timestamp|  | | 创建时间
active | tinyint(1) | un | | 删除标识



## agt_agent_festival_images

代理商节气二维码

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
agent_id | int(11)|  | | 代理商ID
festival_year| char(4) |  | | 年份
festival_date | datetime |  | | 节日时间
festival_title | varchar(50) |  | | 节日名称
festival_image_url | varchar(250)| | | 节日图片链接地址
festival_refer_url | varchar(250) |  | | 一元体验推荐二维码
refer_is_finished | tinyint(1) |  | | 一元体验生成状态
is_finished | tinyint(1) | un | | 生成状态
created_at | timestamp |  | | 创建时间

is_finished

- 1:待生成;
- 0:已生成;
- 2:生成中

refer_is_finished

- 1 : 待生成;
- 0 : 已生成;
- 2 : 生成中



## agt_agent_share_records

代理商用户注册分成，充值分成记录表
此表来源

- clt_customer_recharge_orders 用户充值记录
- clt_customer_register_orders 用户注册付费记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
agent_id | int(11) | un | | 代理商ID
client_customer_id | int(11) | un | | 组织用户ID
customer_type | tinyint(1) | unsigned |  | 注册用户类别
customer_mobile  | varchar(50) | | | 用户手机
payment_type | tinyint(1) | | | 支付类型
payment_amount | bigint(11) | | | 支付金额
share_amount | bigint(11) | | | 分成金额
is_locked | tinyint(1) | | | 是否冻结
share_type | tinyint(1) | | | 分成类型
share_type_id | int(11) | | | 记录对应ID
refer_type | tinyint(1) | | | 分成来源
refer_id | int(11) | | | 分成来源ID
share_source | varchar(20) | | | 分成来源标题
share_date | varchar() | | | 付费日期
share_time | timestamp | | | 付费时间
created_at | timestamp | | | 记录创建时间

payment_type 支付方式

- 1.支付宝，
- 2.微信，
- 3.余额

share_type 分成类型, 此类型决定 share_type_id 的值

- 1 购买会员
- 2 金币充值

refer_type 为推荐类型

- 1: 用户推荐
- 2: 代理商推荐
- 3: 代理商合伙人推荐
- 4: 代理商子账号推荐
- 5: 企业切换
- 20: 下级代理商(金)推荐
- 21: 下级代理商(银铜)推荐

is_locked 是否冻结

- 0 : 未冻结
- 1 : 冻结

customer_type

- 2.社群体验版用户(1)
- 3.社群标准版用户(398)
- 5.社群尊享版用户(798)


## agt_cooperators

伙伴账户表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto | 自增ID
cooperator_type | tinyint(1) |  |  | 伙伴类型
cooperator_mobile | varchar(50) |  |  | 手机号码
cooperator_name | varchar(50) |  |  | 伙伴姓名
cooperator_avatar | varchar(255) | | | 伙伴头像
is_locked  | tinyint(1) |  |  | 是否锁定
created_at | timestamp |  |  | 创建日期
updated_at | timestamp |  |  | 更新日期
active | tinyint(1) | un | | 删除标识

cooperator_type 伙伴类型
- 1 : 代理商
- 2 : 代理商子账号
- 3 : 老师账号
- 4 : 自由合伙人

is_locked 是否锁定
- 1 : 锁定
- 2 : 未锁定

## agt_cooperator_details

伙伴详情表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto | 自增ID
cooperator_id | int(11) | un | | 伙伴ID
real_name | varchar(50) |  |  | 伙伴姓名
bank_name | varchar(255) | | | 开户行名称
bank_account | varchar(100) | | | 银行账号
back_cart_image | varchar(255) | | | 银行卡正面照片
created_at | timestamp|  | | 创建日期
created_by | int(11)|  | | 创建者
updated_at | timestamp|  | | 修改日期
updated_by | int(11)|  | | 修改者




## agt_agent_cooperators

伙伴-代理商 关系表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto | 自增ID
agent_id | int(11) | un | | 所属代理ID
cooperator_id | int(11) | un | | 伙伴ID
created_at | timestamp |  |  | 创建日期
active | tinyint(1) | un | | 删除标识

## agt_cooperator_packs

老师-课程关系表，本表只适用于 cooperator_type 为 3 的伙伴

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto | 自增ID
pack_id | int(11) | un | | 课程ID
cooperator_id | int(11) | un | | 伙伴ID
shared_scale | int(11) | un | | 分成百分比
shared_cut  | int(11) | un | | 订阅分成金额
created_at | timestamp |  |  | 创建日期

## agt_cooperator_share_images

伙伴分享图

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto | 自增ID
cooperator_id | int(11) | un | | 伙伴ID
original_image_url | varchar(255) | | | 分享原始图
share_image_url | varchar(255) | | | 二维码分享图
generate_status | tinyint(1) | | | 生成状态
created_at | timestamp |  |  | 创建日期
updated_at | timestamp |  |  | 更新日期
active | tinyint(1) | un | | 删除标识

generate_status：
- 1:待生成;
- 0:已生成;
- 2:生成中

## agt_cooperator_devices

伙伴app设备号

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
cooperator_id | int(11) | un | | 伙伴ID
device_uuid | varchar(100) |  |  | 设备UUID
operate_system | varchar(100) |  | | 操作系统
operate_version | varchar(100) |  |  | 操作系统版本
app_version | varchar(100) |  | | app版本
device_model | varchar(100) |  |  | 设备型号
registration_id | varchar(200) |  |  | 极光推送设备ID
device_resolution | varchar(50) |  | | 分辨率
created_at | timestamp |  |  | 创建时间

<font color="red">

## agt_cooperator_share_customers

伙伴推广注册用户分成记录
此表来源自
- clt_customer_recharge_orders 用户充值记录，根据推广类型为伙伴的记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
cooperator_id | int(11) | un | | 伙伴ID
cooperator_type | tinyint(1) |  |  | 伙伴类型
client_customer_id | int(11) | un | | 组织用户ID
customer_type | tinyint(1) | unsigned |  | 注册用户类别
customer_mobile  | varchar(50) | | | 用户手机
payment_type | tinyint(1) | | | 支付类型
payment_amount | bigint(11) | | | 支付金额
share_amount | bigint(11) | | | 分成金额
register_order_id | int(11) | un | | 支付订单ID
is_locked | tinyint(1) | | | 是否冻结
unlock_time   | timestamp | | | 解冻时间
joined_at  | timestamp | | | 用户注册时间
created_at | timestamp | | | 记录创建时间

is_locked 是否冻结

- 0 : 未冻结
- 1 : 冻结

customer_type

- 2.社群体验版用户(1)
- 3.社群标准版用户(398)
- 5.社群尊享版用户(798)



</font>

<font color="red">

## agt_cooperator_pack_monthly_settlements
合伙人（老师）课程月结算

数据来源： 
- agt_agent_port_operations 企业开户端口数+企业扩容端口数，结算为课程订阅，给老师
- clt_customer_packs 用户课程解锁记录（全部解锁，部分解锁，兑换，课程券），结算为课程购买和课程订阅，给老师（略复杂）
- clt_client_packs 企业课程发布记录，结算为课程订阅，给老师


字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
cooperator_id | int(11) | un | | 伙伴ID
cooperator_type | tinyint(1) | un |  | 伙伴类型
pack_id | int(11) | un | | 课程id
pack_name | varchar(50) | un | | 课程名
year | int(11) | un | | 年份
month | int(11) | un |  | 月份
total_sale  | int(11) | un | | 课程销量
settle_amount | bigint(11) | un | | 结算金额
created_at | timestamp | | | 记录创建时间


## agt_cooperator_customer_register_monthly_settlements
合伙人用户注册月结算

数据来源： 
- clt_customer_register_orders 用户注册记录，结算为用户注册


字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
cooperator_id | int(11) | un | | 伙伴ID
cooperator_type | tinyint(1) | un |  | 伙伴类型
year | int(11) | un | | 年份
month | int(11) | un |  | 月份
total_member  | int(11) | un | | 推荐人数
settle_amount | bigint(11) | un | | 结算金额
created_at | timestamp | | | 记录创建时间


## agt_cooperator_customer_recharge_monthly_settlements
合伙人用户充值月结算

数据来源： 
- clt_customer_recharge_orders 用户充值记录，结算为用户充值，给合伙人


字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
cooperator_id | int(11) | un | | 伙伴ID
cooperator_type | tinyint(1) | un |  | 伙伴类型
year | int(11) | un | | 年份
month | int(11) | un |  | 月份
total_member  | int(11) | un | | 充值人次
settle_amount | bigint(11) | un | | 结算金额
created_at | timestamp | | | 记录创建时间


## agt_cooperator_monthly_settlements

合伙人月结算记录（一个月一条，是否必要？）

数据来源：
- agt_cooperator_pack_monthly_settlements 
- agt_cooperator_customer_recharge_monthly_settlements
- agt_cooperator_customer_register_monthly_settlements


字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
cooperator_id | int(11) | un | | 伙伴ID
cooperator_type | tinyint(1) |  |  | 伙伴类型
year | int(11) | un | | 年份
month | int(11) | un |  | 月份
settle_amount | bigint(11) | | | 分成金额
created_at | timestamp | | | 记录创建时间


## agt_cooperator_quarter_issues

合伙人季度发放记录

数据来源：月结合计


字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
cooperator_id | int(11) | un | | 伙伴ID
cooperator_type | tinyint(1) |  |  | 伙伴类型
year | int(11) | un | | 年份
quarter | int(11) | un |  | 季度
date_start | date | | | 季度起始日
date_end | date | | | 季度结束日
issue_amount | bigint(11) | | | 发放金额
created_at | timestamp | | | 记录创建时间


</font>

<font color="red">
代理商兑换码批次审核表

## agt_agent_redeem_code_batchs

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 批次id
agent_id | int(11) | un | | 代理商id
batch_level_one_id | int(11) | un |  | 一级代理商ID
batch_level_two_id | int(11) | un |  | 二级代理商ID
from_agent_id | int(11) | un |  | 转出代理商
to_agent_id | int(11) | un |  | 转入代理商
start_code_number | varchar(50) |  |  | 兑换码开始流水号
end_code_number | varchar(50) |  | | 兑换码结束流水号
redeem_code_amount | int(11) |  |  | 兑换码数量
batch_type | tinyint(1) |  | | 0：平台转移  1：代理商转移
transfer_batch_status | tinyint(1) |  |  | 0: 未审批；1：初审通过；2：初审拒绝；3：复审通过；4：复审拒绝
dispatch_batch_status | tinyint(1) |  |  | 0：未审批 1：已通过 2：已拒绝
request_time | timestamp |  | | 发起请求时间
request_platform_user_id | int(11) |  | | 发起请求者
approval_time | timestamp |  | | 通过请求时间
item_type | tinyint(1) |  | | 1：精英会员；2：定向课程卷；3：课程卷数量；金币数量
item_content | varchar(500) |  | | 1，3，4：为数值   2：以|分割的课程id
reason | varchar(500) |  | | 申请原因
expired_time | timestamp |  | | 过期时间
generate_status | tinyint |  | | 生成状态 0 未开始 1 生成中 2已完成
excel_url | timestamp |  | | excel地址


兑换码分发审核表
## agt_agent_redeem_code_dispatch_check_records

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 批次id
batch_id | int(11) | un | | 批次id
batch_status | tinyint(1) |  |  | 审核状态
check_platform_user_id | int(11) |  | | 审批者id
comment | varchar(500) |  |  | 备注
to_agent_id | int(11) |  | | 被分发代理商
created_at | timestamp |  |  | 创建时间

兑换码转移审核记录
## agt_agent_redeem_code_transfer_check_records

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 批次id
batch_id | int(11) | un | | 批次id
batch_status | tinyint(1) |  |  | 审核状态
check_platform_user_id | int(11) |  | | 审批者id
comment | varchar(500) |  |  | 备注
from_agent_id| int(11) |  | | 分发代理商
to_agent_id | int(11) |  | | 被分发代理商
created_at | timestamp |  |  | 创建时间

兑换码分发表
## agt_agent_redeem_code_dispatch_records

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 批次id
batch_id | int(11) | un | | 批次id
to_agent_id | int(11) |  | | 被分发代理商
created_at | timestamp |  |  | 创建时间

兑换码转移记录
## agt_agent_redeem_code_transfer_records

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 批次id
batch_id | int(11) | un | | 批次id
from_agent_id| int(11) |  | | 分发代理商
to_agent_id | int(11) |  | | 被分发代理商
created_at | timestamp |  |  | 创建时间


代理商为客户扩容记录
## agt_port_allocate_records
字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | id
agent_id | int(11) | un | | 代理商id
client_id | int(11) | un | | 客户id
port_amount | int(11) | un | | 扩容端口数
pack_amount | int(11) | un | | 课程加速数量
content_amount | int(11) | un | | 书籍加速数量
port_point | int(11) | un | | 每端口消耗点数
port_payment | bigint(11) | un | | 每端口支付金额
client_actived_years | int(11) | un | | 客户已活跃年数
client_has_years | int(11) | un | | 客户剩余年数
payment_amount | bigint(11) | un | | 代理商支付的金额
order_id | int(11) | un | | 扩容订单id
allocate_time | timestamp | | | 扩容时间
created_at | timestamp |  |  | 创建时间

客户已活跃年数：参考周岁，第一年为0，第二年为1，第三年为2
若期间有一年处于过期状态，不视为一年

客户剩余年数：包括当前年，之后还有多少年。

扩容时间：因为扩容订单可能延迟支付，为保证计算准确，扩容时间为下单时间

## 代理商为客户扩容支付订单
## agt_port_allocate_orders
字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | id
agent_id | int(11) | un | | 代理商id
client_id | int(11) | un | | 客户id
port_amount | int(11) | un | | 扩容端口数
pack_amount | int(11) | un | | 课程加速数量
content_amount | int(11) | un | | 书籍加速数量
port_point | int(11) | un | | 每端口点数
port_payment | bigint(11) | un | | 每端口支付金额
lock_port_point_amount | int(11) | un | | 冻结购买的端口点数
lock_plt_port_point_amount | int(11) | un | | 冻结赠送的端口点数
lock_leave_point_amount | int(11) | un | | 冻结零余的点数
client_actived_years | int(11) | un | | 客户已活跃年数
client_has_years | int(11) | un | | 客户剩余年数
payment_amount | bigint(11) | un | | 支付金额
payment_type | tinyint(1) | un | | 支付方式
payment_status | tinyint(1) | un | | 支付状态
order_status | tinyint(1) | un | | 履单状态
operate_by | int(11) | un | | 创建人
created_at | timestamp |  |  | 创建时间


客户已活跃年数：参考周岁，第一年为0，第二年为1，第三年为2
若期间有一年处于过期状态，不视为一年

客户剩余年数：包括当前年，之后还有多少年。


</font>

# Domain Client
## clt_clients

客户账号

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto | 自增ID
agent_id | int(11) | un | | 所属代理ID
client_name | varchar(50) |  | | 客户名称
client_pass | varchar(100) |  |  | 客户密码
client_logo | varchar(255) |  |  | 公司logo URL
real_name | varchar(50) |  | | 联系人姓名
company_name | varchar(100) |  | | 公司名称
company_short | varchar(50) |  |  | 公司简称
trial_expired_time | timestamp |  |  | 试用过期时间
enable_time | timestamp |  | | 端口启用日期
expired_time | timestamp|  | | 端口过期日期
client_phone | varchar(50) |  |  | 电话
client_mobile | varchar(50) |  |  | 手机
port_total | int(11) | un | | 端口总数（冗余）
port_amount |int(11) | un | | 已分配端口数
port_inventory | int(11) | un |  | 端口余额
authorize_paper | varchar(255) |  |  | 客户确认单下载地址
storage_total | bigint(11) |  | | 容量总额
storage_used | bigint(11) |  | | 已使用容量
bandwidth_total | bigint(11) |  |  | 流量总额
bandwidth_used | bigint(11) |  |  | 已使用流量
receipt_balance | bigint(11) |  | | 可开发票余额
content_group_id | int(11) |  | | 客户初始化书籍组合ID
pack_id | int(11) |  |  | 客户初始化课程ID
enable_department | tinyint(1) |  |  | 是否开启部门
last_login | timestamp |  |  | 最后登录时间
client_report_status | tinyint(1) |  | | 体验用户数据报表生成标识
client_report_url | varchar(255) |  | | 体验用户报表URL
account_type | tiny(1) |  |  | 账号种类
account_status | tiny(1) |  |  | 账号状态
enable_assignment_lookback | tiny(1) |  | | 是否开启作业本回看
content_publish_inventory | int(11) | un | | 客户内容发布剩余数量
content_publish_total | int(11) | un |  | 客户内容发布总数量
pack_publish_inventory | int(11) | un |  | 客户课程发布剩余数量
pack_publish_total | int(11) | un | | 客户课程发布总数量
active | tinyint(1) |  | | 删除标识
created_at | timestamp |  |  | 创建日期

account_type 表示客户账号种类

- 0 为企业经典版正式客户
- 1 为企业体验客户
- 2 为社群版体验用户
- 3 为社群版正式用户
- 4 为企业Pro版正式客户

account_status 表示客户账号状态，0为有效客户，1为失效客户，2为被锁定
trial_expired_time 表示体验账户过期时间
是否开启部门:

- 0 未开启
- 1 开启

是否开启作业本回看:
	- 0 未开启
	- 1 开启


client_report_status体验用户数据报表生成标识

- 0 : 已生成
- 1：待生成
- 2：生成中


## clt_client_status_operations

客户状态操作记录表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto | 自增ID
client_id | int(11) | un | | 客户ID
account_type_before | tiny(1) |  | | 更改前类型
account_type_after | tiny(1) |  |  | 更改后类型
account_status_before | tiny(1) |  |  | 更改前状态
account_status_after | tiny(1) |  | | 更改后状态
operate_by | int(11) | un |  | 操作人ID
created_at | timestamp|  | | 操作时间



## clt_client_assignment_lookbacks

客户作业本题目回看表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto | 自增ID
client_id | int(11) | un | | 客户ID
quiz_id | int(11) |  | | 题目ID
assignment_id | int(11) |  |  | 作业本ID
accuracy_rate_avg | int(11) |  |  | 平均正确率百分比
created_at | timestamp|  | | 操作时间



# clt_client_port_operations

客户端口操作表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto | 自增ID
client_id | int(11) | un | | 客户ID
event_type | char(9) |  | | 事件类型
operate_type | char(9) |  |  | 端口操作类型
operate_amount | int(11) | un |  | 操作端口数量
operate_by | int(11) | un | | 操作人ID
created_at | timestamp|  | | 操作时间

event_type 事件类型：
PORT_DISP分配端口给用户

operate_type 操作类型：
ADD 增加库存  MIN 减少库存



## clt_client_customers

客户的用户关系表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto | 自增ID
client_id | int(11) | un | | 客户ID
customer_id | int(11)  | un | | 用户ID
customer_type | tinyint(1) | unsigned |  | 注册用户类别
status | tinyint(1) |  |  | 用户在组织中状态
refer_type | tinyint(1) |  |  | 推荐类型
agent_level_one_id | int(11) | un |  | 一级代理商ID
agent_level_two_id | int(11) | un |  | 二级代理商ID
agent_level_three_id | int(11) | un |  | 三级代理商ID
refer_id | int(11) | un |  | 推荐对象ID
enable_time | int(11) | un |  | 若客户类型为社群版，则为注册时间
expired_time | int(11) | un |  | 过期时间
refer_record_id | int(11) | un |  | 关系记录ID
customer_status | int(11) | un |  | 用户是否被续费锁定
community_customer_status | tinyint(1) | un |  | 社群用户状态
refer_agent_id | int(11) |  | | 推荐代理商ID
refer_customer_id | int(11) |  |  | 推荐用户ID
last_access_time | timestamp |  | | 最后交互时间
active | tinyint(1) |  |  | 删除标识
created_at | timestamp|  | | 创建日期

status 表示用户状态

 - 0 用户正常
 - 1 用户试用过期
 - 2 用户锁定

 customer_status   0正常状态 1续费锁定  2操作锁定

refer_type 为推荐类型

 - 0: 无推荐
 - 1: 用户推荐
 - 2: 代理商推荐
 - 3: 代理商合伙人推荐
 - 4: 代理商子账号推荐



## clt_client_packs

客户购买的课程课程包

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto | 自增ID
client_id | int(11) | un | | 客户ID
pack_id | int(11)  | un | | 课程包ID
<font color="red">pack_type</font> | tinyint(1) | | | 课程类型
is_published | tiny(1) |  |  | 是否发布
is_top | tinyint(1) |  |  | 是否置顶
<font color="red">enable_enterprise</font> | tinyint(1) | | | 企业版显示状态
<font color="red">enable_community</font> | tinyint(1) | | | 社群版显示状态
publish_time | timestamp |  | | 发布日期
publish_rank | int(11) | un |  | 发布序号


is_published：

- 0 已发布；
- 1 未发布； 
- 2 预发布

增加预发布状态，即发布锁定状态，每次需要发布当天凌晨，先设置内容或课程为预发布，发布时直接更新状态

<font color="red">
pack_type 课程类型

- 0 : 必修课
- 1 : 选修课

enable_enterprise， enable_community

- 0 : 不显示
- 1 : 显示  

</font>


## clt_client_contents

客户购买的课程包及内容中，已发布的内容

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_id | int(11) | unsigned | | 客户ID
content_class | tinyint(1)  |  | 0 | 内容归属类型
pack_id | int(11) | unsigned |  | 课程包ID
content_id | int(11)| unsigned |  | 内容ID
is_published | int(11) | unsigned | | 是否发布
likes_total | int(11) | unsigned |  | 客户内容点赞总数
comments_total | int(11) | unsigned | | 客户评论总数
is_top | tinyint(1) |  |  | 是否置顶
publish_time | timestamp|  | | 发布日期
publish_rank | int(11)  | unsigned | | 发布序号
publish_tag | tinyint(1) | unsigned |  | 发布标签
display_flag | tiny(1) | unsigned |  | 显示标识
reader_total | int(11) | unsigned | | 已阅读人数
assignment_id_list | text |  |  | 关联的作业本id列表


is_published：
0 已发布；1 未发布； 2 预发布

增加预发布状态，即发布锁定状态，每次需要发布当天凌晨，先设置内容或课程为预发布，发布时直接更新状态

is_top：
0 否；1 是
disp_flag：
0 不显示；1 显示
content_class 内容归属类型
0：普通内容；1：课程内容



## clt_client_assignments（已废弃）

客户作业本关联表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_id | int(11) | unsigned | | 客户ID
assignment_id | int(11)  | unsigned | | 作业本ID
created_at | timestamp |  | | 作业本发布日期



## clt_client_pack_publish_records

课程发布记录表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_id | int(11) | unsigned | | 客户ID
pack_id | int(11)  | unsigned | | 课程ID
created_at | timestamp |  | | 创建日期



## clt_client_content_publish_records

书籍发布记录表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_id | int(11) | unsigned | | 客户ID
content_id | int(11)  |  | | 内容ID
created_at | timestamp |  | | 创建日期



## clt_client_departments

客户部门

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto | 自增ID
client_id | int(11) | un | | 客户ID
department_title | varchar(50)  |  | | 部门名称
department_rank | int(11) |  | 0 | 部门序号(预留)
department_desc | text |  |  | 部门描述
department_status | tinyint(1) |  | | 部门状态
created_at | timestamp |  |  | 创建日期
modified_at | timestamp |  | | 修改日期
active | tinyint(1) | un |  | 删除标识



## clt_client_materials

企业库资料

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_id | int(11) | unsigned | | 客户ID
content_type | tinyint(1)  | unsigned |  | 资料类型
material_title | varchar(200) |  |  | 资料标题
material_cover | varchar(255)|  |  | 资料封面图
player_cover | varchar(255) |  | | 资料播放器封面图（预留）
material_summary | varchar(255) |  |  | 资料一句话说明
material_url | varchar(255) |  | | 资料地址
material_duration | int(11) |  |  | 资料时长/页数
material_size | bigint(11) |  | | 资料容量，单位B
is_published | tinyint(1)  |  | | 发布状态
publish_time | timestamp |  |  | 发布时间
check_status | tinyint(1) |  |  | 审核状态
status_message | varchar(255) |  | | 理由（若审核不过）
is_top | tinyint(1) |  |  | 是否置顶 0：否 1：是
reader_total | int(11) | unsigned |  | 阅读总人数
created_at | timestamp |  |  | 创建日期
modified_at | timestamp |  | | 修改日期
active | tinyint(1) | unsigned |  | 删除标识


content_type 资料类型

- 0: 所有类型 
- 1：视频 
- 2：音频 
- 3：PDF

publish_status 发布状态

- 0：已发布 
- 1：未发布 
- 2: 视频准备中

check_status  审核状态

- 0： 已审核 
- 1：未审核 
- 2：已封禁


## clt_client_material_operations

企业库审核记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_id | int(11) | unsigned | | 客户ID
material_id | int(11)  | unsigned |  | 资料ID
eventy_type | tinyint(1) | unsigned |  | 事件类型
check_status_from | tinyint(1) | unsigned |  | 操作前审核状态
check_status_to | tinyint(1) | unsigned | | 操作后审核状态
status_message | varchar(255) |  |  | 理由（若审核不过）
publish_status_from | tinyint(1) | unsigned | | 操作前发布状态
publish_status_to | tinyint(1) | unsigned |  | 操作后发布状态
operate_by | int(11) | unsigned | | 操作人ID
operate_by_type | tinyint(1)  | unsigned | | 操作人类型
created_at | timestamp |  |  | 创建日期

event_type 事件类型

- 1 : 资料审核 
- 2： 资料发布

operate_by_type 操作人类型

- 0：总部平台
- 1：代理商
- 2：客户


## clt_client_recharge_records

客户充值记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_id | int(11) | unsigned | | 客户ID
recharge_type | tinyint(1)  |  |  | 价格类型
recharge_size | bigint(11) |  |  | 容量/流量 大小
recharge_cost | bigint(11) |  |  | 充值金额
recharge_unit_cost | bigint(11) |  | | 每GB单价
payment_type | tinyint(11) |  |  | 支付类型
payment_amount | bigint(11) |  | | 支付金额
payment_status | tinyint(1) |  |  | 支付状态
created_at | timestamp |  |  | 创建时间

recharge_type 价格类型
1为存储容量；2为流量
payment_type 支付类型
1：支付宝；2：微信支付
payment_status
0：支付成功；1：待支付；2：支付失败；3：支付过期



## clt_client_recharge_record_details

微信付款/支付宝付款订单详情

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
recharge_record_id | int(11) | unsigned | | 充值记录ID
payment_type | tinyint(1)  | unsigned |  | 支付类型
transaction_id | varchar(50) |  |  | 微信支付订单号
result_code | varchar(20) |  |  | 业务结果
return_code | varchar(20) |  | | 返回状态码
return_msg | varchar(200) |  |  | 返回信息
openid | varchar(200) |  | | 用户标识
trade_type | varchar(20) |  |  | 交易类型
bank_type | varchar(20) |  | | 付款银行
total_fee | bigint(11)  |  | | 订单金额
cash_fee | bigint(11) |  |  | 现金支付金额
time_end | timestamp |  |  | 支付完成时间
trade_no | varchar(100) |  |  | 支付宝交易号
buyer_logon_id | varchar(200) |  | | 买家支付宝账号
total_amount | bigint(11) |  |  | 交易金额
receipt_amount | bigint(11) |  | | 实收金额
gmt_payment | timestamp |  |  | 交易支付时间
buyer_user_id | varchar(50) |  | | 买家在支付宝的用户id
response_code | varchar(50)  |  | | 网关返回码
response_msg | varchar(200) |  |  | 网关返回码描述
fund_bill_list | text |  |  | 交易支付使用的资金渠道

fund_bill_list 有数组元素组成，用|分隔，每个有原始由 fund_channel， amount 组成， 其中使用半角逗号分隔



## clt_client_storage_records

客户容量消费记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_id | int(11) | unsigned | | 客户ID
operate_type | tinyint(1)  | unsigned | | 操作类型
operate_size | bigint(11)  | unsigned | | 操作容量
created_at | timestamp |  | | 操作时间

operate_type操作类型
1：增加容量；2：消费容量

## clt_client_bandwidth_daily_records

客户流量日消费记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_id | int(11) | unsigned | | 客户ID
record_date | date  |  | | 日期
bandwidth_size | bigint(11) | unsigned | | 消费流量



## clt_client_receipts

客户发票

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_id | int(11) | unsigned | | 客户ID
receipt_total  | bigint(11)  |  |  | 发票金额
receipt_type | varchar(50) |  |  | 发票类型
receipt_summary | varchar(255) |  |  | 发票内容
receipt_title | varchar(255) |  | | 发票抬头
receiver | varchar(50) |  |  | 收件人
address_area | varchar(50) |  | | 省市
address_detail | varchar(255) |  |  | 详细地址
receiver_phone | varchar(50) |  |  | 联系电话
receipt_status | tinyint(1) |  | | 发票状态
receipt_time | timestamp |  |  | 开票时间
delivery_number | varchar(50) |  |  | 快递编号
created_at | timestamp |  |  | 创建日期

receipt_status 发票状态
0：已签收；1：开具中；2：快递中；3：已撤回



## clt_client_receipt_operations

发票状态变更记录表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
receipt_id | int(11) | unsigned | 0 | 发票ID
client_id  | int(11) | unsigned | 0 | 客户ID
platform_user_id | varchar(50) |  |  | 平台用户ID
from_status | tinyint(1) |  | 0 | 操作前状态
to_status | tinyint(1) |  | | 操作后状态
created_at | timestamp |  |  | 记录生成时间



## clt_client_addresses

客户地址

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_id | int(11) | unsigned | | 客户ID
receipt_title  | varchar(255)  |  |  | 发票抬头
receiver | varchar(50) |  |  | 收件人
province_code | char(3) |  |  | 省Code
province_name | varchar(50) |  | | 省会名称
city_code | char(3) |  |  | 城市code
city_name | varchar(50) |  | | 城市名称
address_detail | varchar(255) |  |  | 详细地址
receiver_phone | varchar(50) |  |  | 联系电话
is_default | tinyint(1) |  | | 是否默认 0:是 1:否
created_at | timestamp |  |  | 创建日期
active | tinyint(1) |  |  | 删除标识



## clt_client_replenish_records
客户续费记录表
字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id | int(11) | unsigned | auto | 自增id
agent_id  | int(11) | unsigned |      | 代理商ID
client_id  | int(11) | unsigned |      | 客户ID
replenish_port_amount | int(11) | unsigned | | 续费启用的端口数
replenish_time|timestamp|unsigned||续费启用日期
created_at|timestamp|||创建日期

## clt_client_accelerate_orders
客户加速订单表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
agent_id  | int(11) | unsigned |      | 代理商ID
client_id  | int(11) | unsigned |      | 客户ID
accelerate_type | tinyint(1) | unsigned | | 加速类型
content_amount | int(11) | unsigned | 0 | 内容/课程数量
port_amount | int(11) | unsigned | 0 | 总端口数
portpoint_amount| int(11) | un | | 每端口每内容/课程对应点数
created_at | timestamp |  |  | 创建日期


accelerate_type 加速类型

- 0 ：书籍加速
- 1 ：课程加速

## clt_client_accelerate_records
客户加速记录表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_id  | int(11) | unsigned |      | 客户ID
object_id  | int(11) | unsigned |      | 操作对象ID
accelerate_type | tinyint(1) | unsigned | | 加速类型
created_at | timestamp |  |  | 创建日期

accelerate_type 加速类型

- 0 ：书籍加速，此时 object_id 为书籍ID
- 1 ：课程加速，此时 object_id 为课程ID



# Domain Customer

## clt_customers

用户账号

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
customer_mobile | varchar(50) |  | | 用户手机号码
client_id  | int(11)  | unsigned |  | 所属默认客户ID
last_login | timestamp |  |  | 最后登录时间
active | tinyint(1) |  |  | 删除标识
created_at | timestamp |  | | 创建时间



## clt_customer_accounts

用户账户表，金钱类相关

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_id | int(11) | unsigned | | 客户ID
customer_id  | int(11)  | unsigned |  | 用户ID
client_customer_id | int(11) | unsigned |  | 企业用户关系ID
open_id | varchar(50) |  |  | 微信open ID
access_token | varchar(50) |  | | 微信访问凭证
expiration | timestamp |  |  | 凭证过期时间
refresh_token | varchar(50) |  | | 刷新access_token的凭证
union_id | varchar(50) |  |  | 同一公众平台的用户唯一标识
wx_nick_name | varchar(100) |  |  | 微信用户昵称
wx_head_img_url | varchar(255) |  | | 微信用户头像
ali_open_id | varchar(50) |  |  | 支付宝用户id
ali_nick_name | varchar(100) |  |  | 支付宝账户昵称
ali_head_img_url | varchar(255) |  |  | 支付宝账户头像
income_total | bigint(11) | unsigned |  | 收入总额
outlay_total | bigint(11) | unsigned | | 支出总额
cash_inventory | bigint(11) | unsigned |  | 现金余额
refer_qrcode | varchar(200) |  |  | 一元体验推荐二维码
gold_coin_total| int |  |  | 金币总数
gold_coin_inventory | int |  |  | 金币余额


## clt_customer_details

用户详情表，记录常写字段

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_customer_id | int(11) | unsigned |  | 企业用户关系ID
customer_id  | int(11)  | unsigned |  | 用户ID
client_id | int(11) | unsigned | | 用户所属客户ID
customer_name | varchar(50) |  |  | 用户姓名
customer_avatar | varchar(255) |  | | 用户头像
department_id | int(11) | unsigned |  | 部门ID
customer_department | varchar(50) |  | | 用户部门
customer_position | varchar(50) |  |  | 用户职位
customer_status | tinyint(1) |  |  | 用户状态（预留）
learning_point | int(11) | unsigned | | 学习力
learning_time | int(11)| unsigned |  | 学习总时长（单位分钟）
learning_time_video | int(11) |unsigned |  | 视频学习总时长（单位分钟）
learning_time_audio | int(11) | unsigned |  | 音频学习总时长（单位分钟）
learning_day | int(11) | unsigned |  | 持续学习天数
medal_share_image | varchar(500) |  | | 勋章分享图片
ranking_share_image | varchar(500) |  |  | 排名分享图片
ranking_share_image_status | tiny(int) | unsigned |  | 排名分享图片生成状态
content_total | int(11) | unsigned | | 阅读量
video_reading_total | int(11) | unsigned |  | 视频阅读量
audio_reading_total | int(11) | unsigned |  | 音频阅读量
assignment_passed_total | int(11) | unsigned |  | 作业通过量
likes_total | int(11) | unsigned |  | 学习力点赞总数
registration_id | varchar(200) |  | | 极光推送设备ID
feedback_amount | int(11) |  |  | 反馈信息客服回复的数量
assignment_amount | int(11) |  |  | 作业本通过数量
content_assignment_amount | int(11) |  | | 书籍作业本通过数量
pack_assignment_amount | int(11) |  |  | 课程作业本通过数量
refer_qrcode | varchar(255) |  |  | 社群版邀请二维码
share_prise_image_status | tinyint(1) | | | 分享价分享图生成状态
share_prise_image | varchar(255) | | | 非会员升级分享价分享图

ranking_share_image_status
- 0 已生成 状态 最新版本排名分享图已生成
- 1 准备生成 状态
- 2 生成中 状态

feedback_amount 用户反馈信息被客服回复的数量
若被客服回复，则增加此数量；
一旦客户端请求，下发此数量后，清空该值；

## clt_customer_refer_records

用户扫码注册关系记录表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto | 自增ID
customer_id| int(11) | un |  | 用户ID
client_customer_id | int(11) | un |  | 用户组织ID
refer_type | tinyint(11) | un |  | 推荐类型
agent_level_one_id | int(11) | un |  | 一级代理商ID
agent_level_two_id | int(11) | un |  | 二级代理商ID
agent_level_three_id | int(11) | un |  | 三级代理商ID
refer_id | int(11) | un |  | 推荐对象ID
register_order_type | tinyint(11) | un |  | 付款订单类型
register_order_id | int(11) | un |  | 付款订单ID
created_at | timestamp |  | | 生成时间

refer_type 为推荐类型

 - 0: 无推荐
 - 1: 用户推荐
 - 2: 代理商推荐
 - 3: 代理商合伙人推荐
 - 4: 代理商子账号推荐

refer_id 推荐对象ID， 根据 refer_type 的类型而定
register_order_type 付款订单类型

 - 1: 1元会员
 - 2: 398会员
 - 3: 精英会员兑换券

register_order_id 1,2为付款订单ID 3为兑换券id


## clt_customer_pack_assignment_progress

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_id | int(11) | unsigned | | 客户id
customer_id  | int(11)  | unsigned |  | 用户id
client_customer_id | int(11) | unsigned |  | 客户用户id
department_id | int(11) | unsigned |  | 部门ID
pack_id | int(11) | unsigned |  | 课程id
pack_title | varchar(100) |  | | 课程标题
pack_cover | varchar(255) |  | | 课程图片
assignment_amount | int(11) | unsigned |  | 作业本通过数量
is_finished | tinyint(1) |  |  | 完成状态
updated_at | timestamp |  |  | 更新时间




## clt_customer_verifycodes

手机验证码

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
customer_mobile | varchar(50) |  | | 用户手机
verify_code  | char(6)  |  |  | 验证码
code_status | tiny(1) |  | 0 | 是否可用
created_at | timestamp |  | | 生成时间

status 验证码状态: 1 可用 0 不可用


## clt_customer_tokens

用户token

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
customer_id | int(11) | unsigned | | 用户ID
customer_token  | varchar(50)  |  |  | 用户token
token_status | tinyint(1) |  | 0 | token是否可用
created_at | timestamp |  | | 记录生成时间

token_status token 是否可用 1:可用 0：不可用



## clt_customer_devices

用户设备信息

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
customer_mobile | varchar(50) |  | | 手机号
client_customer_id | int(11) | unsigned |  | 企业用户关系ID
customer_id  | int(11)  | unsigned |  | 用户ID
client_id | int(11) | unsigned | | 所属客户ID
device_uuid | varchar(100) |  |  | 设备UUID
operate_system | varchar(100) |  | | 操作系统
operate_version | varchar(100) |  |  | 操作系统版本
app_version | varchar(100) |  | | app版本
device_model | varchar(100) |  |  | 设备型号
registration_id | varchar(200) |  |  | 极光推送设备ID
device_resolution | varchar(50) |  | | 分辨率
phone_type | varchar(50) |  |  | 上网环境
phone_area | varchar(50) |  |  | 地区
created_at | timestamp |  |  | 创建时间



## clt_customer_favorites

用户收藏表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
client_customer_id | int(11) | unsigned |  | 企业用户关系ID
customer_id  | int(11)  | unsigned |  | 用户ID
client_id | int(11) | unsigned | | 客户ID
content_id | int(11) | unsigned |  | 内容ID
content_type | tinyint(1) | unsigned | | 内容类型
content_group | tinyint(1) | unsigned |  | 内容平台组别
pack_id | int(11) | unsigned | | 课程ID
material_id | int(11) | unsigned |  | 企业库资料ID
favorite_title | varchar(50) |  |  | 收藏的名称
favorite_summary | varchar(500) |  | | 收藏的说明
favorite_image | varchar(255) |  |  | 收藏的展示图片
created_at | timestamp |  |  | 收藏日期

content_type 内容类型，0 为内容 1 为视频 2为音频 3为 课程 4为PDF
content_group 内容组别 1 为持悦平台 2为企业自有



## clt_customer_medals

用户勋章

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_customer_id | int(11) | unsigned |  | 企业用户关系ID
customer_id  | int(11)  | unsigned |  | 用户ID
client_id | int(11) | unsigned | | 所属客户ID
category_id | int(11) | unsigned | | 勋章类型ID
medal_id | int(11) | unsigned | | 勋章ID
created_at | timestamp |  | | 创建日期


## clt_customer_assignments

用户作业本

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_customer_id | int(11) | unsigned |  | 企业用户关系ID
customer_id  | int(11)  | unsigned |  | 用户ID
client_id | int(11) | unsigned | | 所属客户ID
assignment_id | int(11) | unsigned | | 作业本ID
pack_id | int(11) | unsigned | | 课程ID
content_id | int(11) | unsigned |  | 内容ID
content_class | tinyint(1) |  | | 内容类型
is_passed | tinyint(1) |  |  | 是否通过作业本
is_read | tinyint(1) |  |  | 是否读过内容
is_done | tinyint(1) |  |  | 是否做过作业本
done_time | timestamp |  | | 做作业的时间
read_time | timestamp |  | | 读内容的时间
publish_time | timestamp |  | | 内容发布的时间
passed_time | timestamp |  | | 通过作业本的时间

is_passed: 0 未通过  1通过
is_done:0 未做  1 已做
is_read:0未读  1已读



## clt_customer_transfer_records

客户交易记录表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_customer_id | int(11) | unsigned | 0 | 企业用户关系ID
customer_id  | int(11)  | unsigned | 0 | 用户ID
client_id | int(11) | unsigned | 0 | 所属客户ID
transfer_type | tinyint(1) | unsigned | 0 | 交易类型
event_type | tinyint(1) | unsigned | 0 | 交易事件类型
event_id | int(11) | unsigned | 0 | 交易事件ID
event_status | tinyint(1) | unsigned | 0 | 交易事件状态
payment_type | tinyint(1) | unsigned |  | 支付方式
transfer_amount | bigint(11) | unsigned |  | 交易金额
created_at | timestamp |  | | 创建日期

transfer_type 交易类型， 1：支出 2：收入
event_type 交易事件类型，目前有 1：打赏 2：提现
event_id 交易事件ID
打赏事件对应打赏的记录ID
payment_type 支付方式，1.支付宝，2.微信，3.余额
event_status 0:生效；1:失效 比如提现申请被拒绝



## clt_customer_content_comments

用户对内容/企业库资料的留言表&感想圈，记录用户对内容的留言（此表有冗余字段）

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
content_group | int(11) | unsigned |  | 内容平台组别
content_type  | tinyint(11)  | unsigned |  | 评论对象类型
content_id | int(11) | unsigned | | 内容ID
material_id | int(11) | unsigned |  | 资料ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
client_id | int(11) | unsigned |  |用户所属客户ID
content_title | varchar(200) |  | | 管理内容或企业库标题
customer_id | int(11) | unsigned |  | 评论用户ID
comment_image | varchar(255) |  |  | 感想圈默认图片
comment_image_summary | varchar(500) |  | | 感谢圈分享图片说明
customer_name | varchar(50) |  |  | 评论用户昵称
customer_avatar | varchar(255) | |  | 评论用户头像
<font color="red">customer_type</font> | tinyint(1) | unsigned |  | <font color="red">评论用户类别</font>
department_id | int(11) |  |  | 部门ID
customer_department | varchar(50) |  |  | 评论用户部门
comment_body | varchar(2000) |  | | 评论内容
likes_total | int(11) | unsigned | 0 | 评论点赞总数
reward_total | int(11) | unsigned | 0 | 评论赞赏总数
reward_amount_total | bingint(11) | unsigned | 0 | 评论赞赏总金额
review_total | int(11) | unsigned | 0 | 评论留言总数
check_status | tiny(1) | unsigned |  | 审核状态
last_update | int(11) | unsigned |  | 最后更新时间戳
created_at | timestamp |  |  | 评论时间
active | tinyint(1) | unsigned | 0 | 删除标识

content_type评论对象类型，0 为内容 1 为视频 2为音频 3为 课程 4为PDF 5为图片
content_group 内容组别 1 为持悦平台 2为企业自有 3为相册
说明：当content_group为3 时，content_id 为 0 ，即该条评论/感想圈信息不关联任何内容
check_status  审核状态
0： 已审核 1：未审核 2：已隐藏


## clt_customer_content_comment_photos

感想圈用户相册

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
comment_id | int(11) | unsigned |  | 评论ID
photo_thumb_url  | varchar(255) |  |  | 缩略图地址
photo_url | varchar(255) |  | | 图片地址
created_at | timestamp |  |  | 回复时间



## clt_customer_content_comment_reviews

用户内容评论的留言（此表有冗余字段）

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
comment_id | int(11) | unsigned |  | 评论ID
review_body  | varchar(500)  |  |  | 留言内容
<font color="red">display_flag</font>  | tinyint  |  |  | 隐藏显示
customer_id | int(11) | unsigned | |用户ID
client_customer_id | int(11) | unsigned | | 用户主键
customer_name | varchar(50) |  | | 用户名称
customer_avatar | varchar(255) |  | | 用户头像
<font color="red">customer_type</font> | tinyint(1) | unsigned |  | <font color="red">用户类别</font>
refer_client_customer_id  | int(11)  | unsigned |  | 用户主键
refer_customer_id | int(11) | unsigned | | 回复用户ID
refer_customer_name | varchar(50) |  | | 回复用户名称
refer_customer_avatar | varchar(255) |  | | 回复用户头像
<font color="red">refer_customer_type</font> | tinyint(1) | unsigned |  | <font color="red">回复用户类别</font>
created_at | timestamp |  | | 回复时间



## clt_customer_content_comment_likes

用户针对评论的点赞操作记录（此表有冗余字段）

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
comment_id | int(11) | unsigned |  | 评论ID
client_customer_id | int(11) | unsigned | | 用户主键
customer_id | int(11) | unsigned | |点赞用户ID
customer_name | varchar(50) |  | | 点赞用户名称
customer_avatar | varchar(255) |  |  | 用户头像
<font color="red">customer_type</font> | tinyint(1) | unsigned |  | <font color="red">用户类别</font>
created_at | timestamp |  |  | 点赞时间点
updated_at | timestamp |  |  | 点赞再次点赞时间
active | tinyint(1) |  |  | 删除标识



## clt_customer_content_comment_rewards

感想圈打赏记录（此表有冗余字段）

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
comment_id | int(11) | unsigned |  | 评论ID
client_customer_id | int(11) | unsigned | | 用户主键
customer_id | int(11) | unsigned | |打赏用户ID
customer_name | varchar(50) |  | | 打赏用户名称
customer_avatar | varchar(255) |  |  | 打赏用户头像
<font color="red">customer_type</font> | tinyint(1) | unsigned |  | <font color="red">打赏用户类别</font>
reward_amount | bigint(11) |  |  | 打赏金额
created_at | timestamp |  |  | 打赏时间




## clt_customer_content_comment_reward_orders

打赏订单（此表有冗余字段）

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
from_client_customer_id | int(11) | unsigned |  | 评论ID
to_client_customer_id | int(11) | unsigned | | 用户主键
comment_id | int(11) | unsigned | |打赏用户ID
payment_type | tinyint(1) | unsigned | | 打赏用户名称
payment_amount | bigint(11) |  |  | 打赏用户头像
payment_status | tinyint(1) | unsigned |  | 打赏金额
created_at | timestamp |  |  | 打赏时间

payment_type：1.支付宝，2.微信，3.余额
payment_status：0.成功，1.待支付，2.失败，3.超时



## clt_customer_content_comment_messages

用户感想圈消息表（此表有冗余字段）

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
comment_id | int(11) |  |  | 评论ID
owner_id  | int(11)  |  |  | 所属企业用户关系ID
comment_review_id | int(11) | unsigned | | 回复ID
client_customer_id | int(11) | unsigned |  | 企业用户关系ID
customer_id | int(11) | unsigned | | 用户ID
client_id | int(11) | unsigned |  |客户ID
message_type | tinyint(11) | unsigned | | 消息类型
customer_name | varchar(50) |  |  | 评论用户昵称
customer_avatar | varchar(255) |  |  | 评论用户头像
<font color="red">customer_type</font> | tinyint(1) | unsigned |  | <font color="red">评论用户类别</font>
message_time | timestamp |  |  | 留言或点赞时间
review_body | varchar(500) |  |  | 留言内容
reward_amount | bigint(11) |  | | 打赏金额
comment_image | varchar(255) |  |  | 感想圈默认图片
comment_body | varchar(2000) |  | | 评论内容
has_read | tiny(1) |  |  | 是否已阅读
created_at | timestamp |  |  | 创建时间
active | tinyint(1) |  | 0 | 删除标识

message_type 消息类型
1：我的感想被评论 2：我的感想被点赞 3:我的感想被打赏 4：我的回复被回复
has_read 是否已读
1：未读 0：已读



## clt_customer_feedback

用户反馈

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
issue_type | tinyint(1) | unsigned |  | 反馈问题类型
issue_type_title  | varchar(50)  |  |  | 反馈问题类型名称
client_customer_id | int(11) | unsigned |  | 企业用户关系ID
customer_id | int(11) | unsigned | | 用户ID
client_id | int(11) | unsigned |  |客户ID
feedback_body | varchar(500) |  | | 反馈内容
feedback_title | varchar(50) |  |  | 手机号码或邮箱
customer_name | varchar(50) |  |  | 用户昵称
customer_avatar | varchar(255) |  |  | 用户头像
<font color="red">customer_type</font> | tinyint(1) | unsigned |  | <font color="red">用户类别</font>
feedback_type | tinyint(1) |  | 0 | 回复类型
root_id | int(11) |  | 0 | 根ID
parent_id | int(11) |  | 0 | 父ID
feedback_status | tinyint(1) |  | 0 | 反馈状态
closed_by | int(11) |  | | 反馈结束ID
device_id | int(11) |  | 0 | 设备ID
created_at | timestamp |  |  | 创建时间
updated_at | timestamp |  |  | 更新日期
active | tinyint(1) |  | 0 | 删除标识

feedback_type 回复类型
0：终端用户回复 1：客服回复
feedback_status 反馈状态
1：客服已回复 2：进行中 9：已结束



## clt_customer_feedback_images

用户反馈

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
feedback_id | int(11) | unsigned |  |用户反馈ID
feedback_image_url  | varchar(250)  |  |  | 用户反馈上传的图片
created_at  | timestamp |  |  | 创建时间



## clt_customer_downloads

用户下载记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_customer_id | int(11) | unsigned |  | 企业用户关系ID
customer_id | int(11) | unsigned | | 用户ID
client_id | int(11) | unsigned | |用户所属客户ID
content_id | int(11) | unsigned | | 内容ID
content_class | tinyint(1) | unsigned |  | 0：普通内容 1：课程内容
content_type | tinyint(1) |  |  | 内容类型
created_at | timestamp |  |  | 创建日期



## clt_customer_content_records

用户阅读详细记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_customer_id | int(11) | unsigned |  | 企业用户关系ID
customer_id | int(11) |  | | 用户ID
client_id | int(11) |  | |用户所属客户ID
content_id | int(11) |  | | 内容ID
start_time | int(11) |  | | 开始阅读位置（单位秒）
end_time | int(11) |  | |结束阅读位置（单位秒）
reading_date | date |  | | 阅读日期
reading_time | timestamp |  |  | 阅读开始时间（客户端）
reading_duration | int(11) |  |  | 本内容阅读时长
content_type | tinyint(1) |  |  | 内容类型
reading_complete | tinyint(1) |  | | 是否完全播放
track_id | varchar(50) |  | | 跟踪同一个内容阅读的ID
created_at | timestamp |  |  | 记录时间

content_type:  1 为视频 2为音频
reading_complete:   1为完全播放，0为未完全播放



## clt_customer_assignment_records

用户完成作业记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_customer_id | int(11) | unsigned |  | 企业用户关系ID
customer_id | int(11) | unsigned | | 用户ID
client_id | int(11) | unsigned | |用户所属客户ID
assignment_id | int(11) | unsigned | | 作业本ID
is_passed | tinyint(1) |  | | 是否通过
assignment_star | tinyint(1) |  | |作业完成星数
assignment_score | int(11) | unsigned | | 作业完成分数
fail_quizs | varchar(100) |  |  | 错题列表
customer_answers | text |  |  | 客户端提交的数据
created_at | timestamp |  |  | 创建日期

is_passed 是否通过 0未通过 1通过
assignment_star 完成星数， 0：未通过 1：1颗星三次以上通过，2： 2颗星，两次通过，3：3颗星，一次通过
failed_quizs 错题列表：1|3|5|9



## clt_customer_assignment_quiz_records

用户作业本题目记录表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
record_id | int(11) | unsigned |  | 记录ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
assignment_id | int(11) | unsigned | |作业本ID
quiz_id | int(11) | unsigned | | 题目ID
is_passed | tinyint(1) |  |  | 是否通过
customer_answer | varchar(200) |  |  | 回答的答案
created_at | timestamp |  |  | 创建日期

is_passed 是否通过 0未通过 1通过



## clt_customer_assignment_quiz_summary

用户题目小计表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
assignment_id | int(11) | unsigned | |作业本ID
quiz_id | int(11) | unsigned | | 题目ID
passed_count | int(11) | unsigned |  | 通过的次数
total_count | int(11) | unsigned |  | 回答的总次数
created_at | timestamp |  |  | 创建日期



## clt_customer_assignment_medal_records

记录用户完成作业本对应的所有勋章

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
customer_id | int(11) | unsigned | |用户ID
client_id | int(11) | unsigned | | 所属客户ID
assignment_id | int(11) | unsigned |  | 作业本ID
medal_category_id | int(11) | unsigned |  | 勋章类别ID
created_at | timestamp |  |  | 创建日期



## clt_customer_report_daily

用户每日报表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
customer_id | int(11) | unsigned | |用户ID
client_id | int(11) | unsigned | | 客户ID
report_date | date |  |  | 日期
learning_point | int(11) | unsigned |  | 点数每日小计
learning_time | int(11) | unsigned |  | 阅读时长（分钟）
content_total | int(11)  | unsigned |  | 每日阅读量



## clt_customer_app_events

用户APP活动事件
字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
customer_id | int(11) | unsigned | |用户ID
client_id | int(11) | unsigned | | 客户ID
trigger_type | tinyint(1) | unsigned | | 事件触发类型
action_type | tinyint(1) | unsigned | | 事件动作类型
action_object | varchar(255) | unsigned | | 时间动作类型对应对象
is_consumed | tinyint(1) | unsigned | | 是否已经消费
consumed_at | timestamp | | current_timestamp | 消费时间
created_at | timestamp |  | current_timestamp | 创建日期

trigger_type 事件触发类型

- 1 : 登陆后弹窗时间

action_type 事件类型
- 1 : 弹出本地画面
- 2 : 加载远程URL

action_object 时间动作类型对应对象
- "customer_398" : 老用户
- "activity_book" : 送书活动




## clt_learning_point_records

用户学习力点数增加或减少记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
customer_id | int(11) | unsigned | |用户ID
client_id | int(11) | unsigned | | 客户ID
report_date | date |  |  | 点数操作日期
event_type | tinyint(1) |  |  | 事件类型
event_id | int(11) |  |  | 事件ID
point_action | char(3)  |  |  | 点数操作类型
point_score | int(11) |  |  | 点数值
summary | varchar(200) |  |  | 点数操作说明
created_at | timestamp  |  |  | 记录日期

event_type 事件类型
1：视频内容看 2：音频内容听 3：作业完成
point_action 点数操作类型， ADD 表示增加 DEL 表示扣除
event_id 若 event_type为视频或者音频， event_id 为内容ID， 若 event_type为作业，则 event_id为作业ID



## clt_learning_point_ranking

用户总排名表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
customer_id | int(11) | unsigned | |用户ID
client_id | int(11) | unsigned | | 所属客户ID
learning_points | int(11) |  |  | 学习力点数



## clt_learning_point_ranking_likes

用户学习力总排名点赞表，对于表 clt_learning_point_ranking的点赞

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
ranking_id | int(11) | unsigned | |总排名ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
customer_id | int(11) | unsigned |  | 点赞用户ID
client_id | int(11) | unsigned | | 所属客户ID
created_at | timestamp |  |  | 创建日期



## clt_learning_point_ranking_weekly

用户周排名表（根据用户点数每周生成，本周数据动态增加）

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
customer_id | int(11) | unsigned |  | 用户ID
client_id | int(11) | unsigned | | 所属客户ID
ranking_year | char(4) |  | | 年份
week_of_year | tiny(2) |  |  | 第几周
learning_points | int(11) | unsigned | | 学习力点数
week_rank | int(11) | unsigned |  | 周排名序号




## clt_learning_point_ranking_weekly_likes

用户学习力周排名点赞表，对于表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
customer_id | int(11) |  |  | 用户ID
client_id | int(11) |  | | 所属客户ID
weekly_id | int(11) |  | | 周统计ID
created_at | timestamp |  |  | 创建时间


## clt_department_ranking

部门总排名表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
client_id | int(11) | unsigned | | 所属客户ID
department_id | int(11) | unsigned | | 部门ID
learning_points | int(11) | unsigned |  | 学习力点数
like_total | int(11) | unsigned | | 点赞总数


## clt_department_ranking_likes

部门总排名点赞表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
ranking_id | int(11) | unsigned |  | 总排名ID
client_id | int(11) | unsigned | | 所属客户ID
department_id | int(11) | unsigned | | 部门ID
created_at | timestamp|  |  | 创建日期



## clt_department_ranking_weekly

部门周排名

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_id | int(11) | unsigned | | 所属客户ID
department_id | int(11) | unsigned | | 部门ID
ranking_year | char(4) |  | | 年份
week_of_year | tiny(2) | unsigned | | 	第几周
learning_points | int(11) | unsigned |  | 学习力点数
like_total | int(11) | unsigned | | 点赞总数
week_rank | int(11) | unsigned |  | 周排名序号



## clt_department_ranking_weekly_likes

部门周排名点赞表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
client_id | int(11) |  | | 所属客户ID
department_id | int(11) | unsigned | | 部门ID
weekly_id | int(11) |  |  | 周统计ID
created_at | timestamp|  | | 创建时间



## clt_customer_blacklist

用户手机黑名单

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
customer_mobile | varchar(50) |  | | 用户手机号码
operate_by | int(11) | unsigned | | 操作人ID
created_at | timestamp|  | | 创建时间
active | tinyint(1) |  |  | 删除标识



## clt_customer_whitelist

用户白名单

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
customer_mobile | varchar(50) |  | | 用户手机号码
customer_code | char(6) |  | | 用户默认验证码
operate_by | int(11) | unsigned | | 操作人ID
created_at | timestamp|  | | 创建时间
active | tinyint(1) |  |  | 删除标识



## clt_customer_content_read_records

用户是否阅读内容的记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
customer_id | int(11) |  | | 用户ID
client_id | int(11) |  | | 所属客户ID
content_id | int(11)|  | | 内容ID
content_type | tinyint(1) |  |  | 内容类型
created_at | timestamp|  | | 记录时间


## clt_customer_material_records

企业库阅读记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
customer_id | int(11) |  | | 用户ID
client_id | int(11) |  | | 所属客户ID
material_id | int(11)|  | | 资料ID
start_time | int(11) |  |  | 开始阅读位置（单位秒）
end_time | int(11)|  | | 结束阅读位置（单位秒）
reading_date | date |  | | 阅读日期
reading_time | timestamp |  | | 阅读开始时间（客户端）
reading_duration | int(11) |  | | 本资料阅读时长/页数
bandwidth_usage | bigint(11) | unsigned | | 消耗流量
reading_complete | tinyint(1) |  |  | 是否完全播放
track_id | varchar(50)|  | | 跟踪同一个内容阅读的ID
created_at | timestamp|  | | 记录时间



## clt_customer_material_records

企业库阅读记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
customer_id | int(11) |  | | 用户ID
client_id | int(11) |  | | 所属客户ID
material_id | int(11)|  | | 资料ID
total_duration | int(11) | unsigned |  | 资料阅读总时长
bandwidth_usage | bigint(11) | unsigned | | 消耗总流量
created_at | timestamp|  | | 记录时间



## clt_customer_material_downloads

用户下载记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
customer_id | int(11) | unsigned | | 用户ID
client_id | int(11) | unsigned | | 所属客户ID
material_id | int(11)| unsigned | | 资料ID
content_type | tinyint(1) |  |  | 内容类型
created_at | timestamp|  | | 记录时间



## clt_customer_cafenotes_coupons

Cafenotes优惠码表 含冗余字段

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
coupon_code | varchar(50) |  | | 优惠码
client_customer_id | int(11) | unsigned | | 企业用户关系ID
coupon_status | tinyint(1) | unsigned | | 优惠码绑定状态



## clt_customer_cafenotes_coupon_records

Cafenotes用户订单记录 含冗余字段

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
coupon_code | varchar(50) |  | | 优惠码
client_customer_id | int(11) | unsigned | | 企业用户关系ID
customer_mobile | varchar(20) | unsigned | | 用户手机号
payment_type | tinyint(1) | unsigned | | 支付类型
payment_status | tinyint(1) | unsigned | | 支付状态
payment_amount | bigint(11) |  |  | 支付金额
created_at | timestamp|  | | 创建日期



## clt_customer_withdraw_records

提现申请订单

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
customer_id | int(11) | unsigned | | 用户id
client_customer_id | int(11) | unsigned | | 企业用户关系ID
audit_status | tinyint(1) | unsigned | | 审核状态
audit_message | varchar(200) |  | | 审核理由
open_id | varchar(50) |  | | 提现用户第三方账户
withdraw_amount | bigint(11) |  |  | 提现申请金额
payment_type | tinyint(1)| unsigned | | 支付类型
payment_status | tinyint(1)| unsigned | | 支付状态
payment_amount | bigint(11) |  |  | 提现实际金额
withdraw_time | timestamp|  | | 成功提现时间
created_at | timestamp|  | | 创建日期

audit_status：0.审核通过 1.待审核 2.审核失败
payment_status：0.成功 1.待支付 2.失败 3.超时
payment_type：1.支付宝 2.微信



## clt_customer_history_records

用户阅读历史记录表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
content_group | tinyint(11) |  | | 内容组别
content_type | tinyint(11) |  | | 内容类型
content_id | int(11) |  | | 内容ID
material_id | int(11) |  | | 企业库资料ID
record_title | varchar(200)|  |  | 内容/资料标题
record_cover_url | varchar(255)|  | | 内容/资料封面图片
end_time | int(11)|  | | 结束阅读/PDF位置（单位秒）
content_total_time | int(11) | unsigned |  | 阅读的内容/资料总时长
record_time | timestamp|  | | 创建日期
active | tinyint(1)|  | | 删除标识

content_group 内容组别
1 为持悦平台 2为企业自有

content_type 内容类型
0 为内容 1 为视频 2为音频 3为 课程 4为PDF




## clt_customer_achievements

用户成就

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
customer_id | int(11) | unsigned | | 用户ID
client_id | int(11) | unsigned | | 所属客户ID
achievement_id | int(11) |  | | 成就id
share_image_status | varchar(255) |  | | 分享图片生成状态
share_image | varchar(255)|  |  | 分享图片
passed_rules | varchar(255)|  | | 改成就已通过的规则id
is_win | tinyint(1)|  | | 是否获得该成就
created_at | timestamp |  |  | 创建时间
active | tinyint(1)|  | | 删除标识

is_win  0:未获取    1：已获取
share_image_status   0:未开始生成   1：生成中  2：已生成



## clt_customer_messages


字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
customer_id | int(11) | unsigned | | 用户ID
client_id | int(11) | unsigned | | 所属客户ID
message_type | tinyint | unsigned | | 消息类型
is_read | tinyint | unsigned | | 是否阅读
action_to | varchar(255)|  |  | 跳转id或者url
read_time | timestamp|  | | 阅读时间点
message_title | varchar(50) |  | | 消息标题
message_body | varchar(500) |  | | 消息体
created_at | timestamp |  |  | 创建时间
active | tinyint(1)|  | | 删除标识

message_type  1：欢迎  2：勋章  3：签到  4：书籍  5：课程  6：解锁  7：提现  8：消息反馈
is_read   0：未读  1：已读
active   0:删除  1：未删除



## clt_customer_trial_records

一元体验申请单

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
refer_type | tinyint(1) | unsigned | | 推荐类型
refer_agent_id | int(11) | unsigned | | 推荐代理商id
refer_client_customer_id | int(11) | unsigned | | 推荐人clientCustomerId
customer_mobile | varchar(50) |  | | 用户手机号
customer_name | varchar(50) |  | | 用户姓名
client_id | int(11) | unsigned |  | 绑定体验企业id
trial_status | tinyint(1) | unsigned | | 用户体验状态
trial_expired_time | timestamp |  | | 试用过期时间
guide_type | tinyint(1) | unsigned | | 引导类型：0：个人，1：企业
payment_type | tinyint(1) | unsigned |  | 支付类型
payment_status | tinyint(1)|  | | 支付状态
payment_amount | bigint(11) |  |  | 提现实际金额
created_at | timestamp |  | | 创建日期

refer_type 推荐类型（自然流量不会进入这里）
0: 自然流量 1: 代理商推荐 2: 用户推荐

trial_status：0.体验中 1.代开户 2.引导中 3.体验结束
guide_type：0.个人 1.企业
payment_status：0.成功 1.待支付 2.失败 3.超时
payment_type：1.支付宝 2.微信



## clt_customer_share_images

个人分享图片

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_customer_id | int(11) | unsigned | | 组织用户id
share_url | varchar(255) |  | | 分享图片url
template_type | tiny(1) | | 0 | 模板类型
template_id | int(11) | unsigned | | 模板id
template_status | tinyint(1) | unsigned | | 模板状态（上架下架）
generate_status | tinyint(1) | unsigned | | 图片生成状态
created_at | timestamp |  | | 创建日期


template_type:

- 0: 用户注册邀请分享图
- 1: 课程注册邀请分享图

当 template_type 为 0 时， template_id 为 pack_id
当 template_type 为 1 时， template_id 为


template_status：

- 0.上架
- 1.下架

generate_status：
- 1:待生成;
- 0:已生成;
- 2:生成中

## clt_customer_register_orders

用户注册订单

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
refer_type | tinyint(1) | unsigned | | 推荐类型
agent_level_one_id | int(11) | unsigned | | 一级代理商id
agent_level_two_id | int(11) | unsigned | | 二级代理商id
agent_level_three_id | int(11) | unsigned | | 三级代理商id
refer_id | int(11) | unsigned | | 推荐人id
refer_agent_id | int(11) | unsigned | | 推荐代理商ID
client_id | int(11) | unsigned | | 注册组织id
customer_type | tinyint(1) | unsigned |  | 注册用户类别
customer_mobile | varchar(20) |  | | 用户手机号
payment_type | tinyint(1) | unsigned |  | 支付类型
payment_status | tinyint(1)| unsigned | | 支付状态
payment_amount | bigint(11) |  |  | 提现实际金额
<font color="red">is_locked | tinyint(1) | | | 是否冻结 </font>
created_at | timestamp |  | | 创建日期

refer_type：

- 0.无推荐
- 1.用户推荐
- 2.代理商推荐
- 3.代理商合伙人推荐
- 4.代理商子账号推荐

customer_type：

- 2.社群体验版用户(1) 
- 3.社群标准版用户(398) 
- 5.社群尊享版用户(798)
- 其他枚举：
- 0.企业标准版用户 
- 1.企业体验版用户 
- 4.企业Pro版用户

payment_status：0.成功 1.待支付 2.失败 3.超时
payment_type：1.支付宝 2.微信

<font color="red">
is_locked 是否冻结

- 0 : 未冻结
- 1 : 冻结
</font>



## clt_customer_packs

用户课程

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id|int| ||自增id
<font color="red">client_id | int | | |  客户id  </font>
<font color="red">customer_id | int | | | 用户id </font>
client_customer_id|int|||客户用户id
pack_id|int|||课程Id
<font color="red">pack_type | int | | | 课程类型 </font>
unlock_type|int|||0:课时卷解锁或者金币挨个解锁  1:课程卷解锁  2：金币一次性解锁
unlock_refer_id|int|||对应ID，若优惠券解锁，则为couponID，若为金币购买解锁，则为Order ID
unlock_time|datetime|||解锁时间
lock_status|int|||解锁状态  0未解锁  1部分解锁  2已解锁

unlock_type  0:课时卷解锁或者金币挨个解锁  1:课程卷解锁  2：金币一次性解锁

lock_status  解锁状态  0未解锁  1部分解锁  2已解锁

<font color="red">
pack_type 课程类型
- 0 : 必修课
- 1 : 选修课
</font>

## clt_customer_contents

用户内容

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id|int|||自增id
<font color="red">client_id | int | | | 客户id</font>
<font color="red">customer_id | int | | | 用户id</font>
client_customer_id|int|||用户客户id
content_class|int|||内容类型
pack_id|int|||课程id
content_id|int|||内容id
unlock_type|int|||解锁类型
unlock_refer_id|int|||对应ID，若优惠券解锁，则为couponID，若为金币购买解锁，则为Order ID
unlock_time|timestamp|||解锁时间

unlock_type  解锁类型  1:书籍卷 2：课时卷 3：课程卷  4：体验书籍券 5：体验课时券 6：体验课程券 7：金币


## clt_customer_recharge_orders

金币充值记录表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id|int|||自增id
client_id|int|||客户id
customer_id|int|||用户id
client_customer_id|int|||用户客户id
refer_type | tinyint(1) |  |  | 推荐类型
agent_level_one_id | int(11) | un |  | 一级代理商ID
agent_level_two_id | int(11) | un |  | 二级代理商ID
agent_level_three_id | int(11) | un |  | 三级代理商ID
refer_id | int(11) | un |  | 推荐对象ID
refer_agent_id | int(11) |  | | 推荐代理商ID
gold_coin_amount|int|||金币金额
<font color="red">is_locked | tinyint(1) | | | 是否冻结 </font>
payment_type|int|||支付类型   1：支付宝 2：微信  3：余额  4：苹果支付
payment_amount|bigint|||支付金额
payment_status|int|||支付状态
order_time|timestamp|||订单时间

payment_type  支付类型  0：余额 1：支付宝 2：微信  3：苹果支付

<font color="red">
is_locked 是否冻结

- 0 : 未冻结
- 1 : 冻结
</font>



## clt_customer_gold_coin_records

用户金币收入记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id|int|||自增id
client_id|int|||客户id
customer_id|int|||用户id
client_customer_id|int|||用户客户id
gold_coin_amount|int|||金币金额
record_type|int|||获取类型   1：支付宝充值 2微信充值 3苹果支付 4：兑换码兑换
record_id|int|||获取ID
created_at|timestamp|||新建时间

<font color="red">
record_type  获取类型   
- 1：支付宝充值
- 2：微信充值
- 3：苹果支付
- 4：兑换码兑换
</font>

## clt_customer_consume_records

用户金币消费记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id|int|||自增id
client_id|int|||客户id
customer_id|int|||用户id
client_customer_id|int|||用户客户id
gold_coin_amount|int|||金币金额
consume_type|int|||消费类型   1：书籍 2：课时  3：课程
consume_object_id|int|||消费对象ID
created_at|timestamp|||新建时间

consume_type   消费类型   1：书籍 2：课时  3：课程

## clt_customer_coupons

用户优惠券

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id|int|||自增id
client_id|int|||客户id
customer_id|int|||用户id
client_customer_id|int|||客户用户id
coupon_source|int|||优惠券来源  1：开户赠送 2: 兑换码兑换
coupon_type|int|||优惠券类型	1:书籍卷 2：课时卷 3：课程卷
coupon_status|int|||优惠券状态   1：未使用 2：已使用  3：已过期
fetch_time|int|||获取时间
consume_time|timestamp|||消费时间
expired_time|timestamp|||过期时间

coupon_status 优惠券状态   1：未使用 2：已使用  3：已过期
<font color="red">
coupon_source 优惠券来源  

- 1：开户赠送
- 2: 兑换码兑换

</font>

coupon_type  	优惠券类型	1:书籍卷 2：课时卷 3：课程卷  4：体验书籍券 5：体验课时券 6：体验课程券

## clt_customer_invitations
受邀请开户表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id|int|||自增id
client_id|int|||客户id
customer_id|int|||用户id
client_customer_id|int|||用户客户id
invited_status|int|||0未发邀请，1已发邀请，2已被他人邀请
gold_coin_amount|int|||邀请成功后可以获得的金币数量
invited_customer_type|tiny|||受邀请人的类型  1：体验用户   2：正式会员
invited_client_customer_id|int|||受邀请人的id
created_at|timestamp|||创建时间

invited_status  0未发邀请，1已发邀请，2已被他人邀请
invited_customer_type 1：体验用户   2：正式会员


## clt_customer_openid_token
发送微信分享表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id|int|||自增id
openid|int|||微信openId
token|int|||唯一token码
refer_type|int|||分享类型
is_shared|int|||0未分享 1已分享
refer_id|int|||来自分享人的id
created_at|timestamp|||创建时间

refer_type   0无推荐  1用户推荐  2代理商推荐  3代理商合伙人推荐  4代理商子账号推荐
is_shared   0未分享 1已分享

## clt_customer_campaign_records
用户参与活动记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id|int(11)|||自增id
campaign_id|int(11)|||活动id
client_customer_id|int(11)|||用户账户id
created_at|timestamp|||创建时间

## clt_customer_comment_blocks

用户感谢圈屏蔽列表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id|int(11)|||自增id
client_id|int(11)|||组织id
customer_id|int(11)|||用户id
client_customer_id|int(11)|||用户账号id
blocked_client_customer_id|int(11)|||被屏蔽的人
customer_name | varchar(50) |  |  | 被屏蔽的用户姓名
customer_avatar | varchar(255) |  | | 被屏蔽的用户头像
blocked_status|tinyint(1)|||过滤状态 0.放行；1.感想圈屏蔽；
updated_at|timestamp|||更新时间
created_at|timestamp|||创建时间

block_status 屏蔽状态

- 0.放行
- 1.感想圈屏蔽


## clt_customer_share_records

用户分享记录表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id|int(11)|||自增id
client_id|int(11)|||组织id
customer_id|int(11)|||用户id
client_customer_id|int(11)|||用户账号id
shared_type|int(11)|||分享类型
created_at|timestamp|||创建时间

shared_type 1:周排行 2:月排行 3:总排行 4:成就分享 5:书籍分享 6:课时分享
7:课程分享  8:邀请好友加入分享  9:分享价升级分享 10:感想圈分享

## clt_department_ranking_monthly

部门周排名

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_id | int(11) | unsigned | | 所属客户ID
department_id | int(11) | unsigned | | 部门ID
ranking_year | char(4) |  | | 年份
month_of_year | tiny(2) | unsigned | | 	第几周
learning_points | int(11) | unsigned |  | 学习力点数
like_total | int(11) | unsigned | | 点赞总数
month_rank | int(11) | unsigned |  | 月排名序号
last_month_rank| int(11) | unsigned |  | 上月排名序号


## clt_department_ranking_monthly_likes

部门周排名点赞表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
client_id | int(11) |  | | 所属客户ID
department_id | int(11) | unsigned | | 部门ID
monthly_id | int(11) |  |  | 周统计ID
created_at | timestamp|  | | 创建时间

## clt_learning_point_ranking_monthly

用户周排名表（根据用户点数每周生成，本周数据动态增加）

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto | 自增ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
customer_id | int(11) | unsigned |  | 用户ID
client_id | int(11) | unsigned | | 所属客户ID
ranking_year | char(4) |  | | 年份
month_of_year | tiny(2) |  |  | 第几周
learning_points | int(11) | unsigned | | 学习力点数
month_rank | int(11) | unsigned |  | 月排名序号
last_month_rank | int(11) | unsigned |  | 上月排名序号



## clt_learning_point_ranking_monthly_likes

用户学习力周排名点赞表，对于表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
customer_id | int(11) |  |  | 用户ID
client_id | int(11) |  | | 所属客户ID
monthly_id | int(11) |  | | 周统计ID
created_at | timestamp |  |  | 创建时间


</font>


<font color="red">

## clt_customer_redeem_code_records
用户兑换码使用记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
client_customer_id | int(11) | unsigned | | 企业用户关系ID
agent_id | int(11) | unsigned | | 拥有改兑换码的代理商
redeem_code_title | varchar(100) |  |  | 兑换码
redeem_code_number | int(11) |  |  | 兑换码
created_at | timestamp |  |  | 创建时间
</font>



<font color="red">

## clt_customer_agents
用户代理商关联表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto | 自增ID
customer_id | int(11)  | un | | 用户ID
customer_mobile | varchar(50)  |  | | 用户手机号
agent_level_one_id | int(11) | un |  | 一级代理商ID
agent_level_two_id | int(11) | un |  | 二级代理商ID
agent_level_three_id | int(11) | un |  | 三级代理商ID
agent_id | int(11) |  | | 代理商ID
enable_status | tinyint(1) |  |  | 是否启用
created_at | timestamp|  | | 创建日期
created_by | int(11)|  | | 创建者
updated_at | timestamp|  | | 修改日期
updated_by | int(11)|  | | 修改者
active | tinyint(1) |  |  | 删除标识



enable_status ： 0:未启用,1:已启用,2:已停用

</font>


## ntc_notification_records

消息推送记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned |  | 自增ID
notify_status  | tinyint(1) |  | | 消息发送状态
push_platform | varchar(10) |  | | 发送平台类型
event_type | tinyint(1) |  | | 消息类型
target_type | varchar(100) |  |  | 目标类型
target_value | varchar(50) |  |  | 目标标识符
registration_id | varchar(200) |  |  | 设备ID
message_body | varchar(1024)|  |  | 消息体
message_id| varchar(20) |  | | 推送id
created_at | timestamp |  |  | 创建日期


notify_status 发送状态

 - 0 ： 已发送
 - 1 ： 未发送




# Domain Payment

## pmt_payment_orders

支付订单记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned |  | 自增ID
open_id | varchar(50) |  | | 支付平台用户
trade_no| varchar(32) |  | | 支付平台反馈的订单号
out_trade_no | varchar(32) |  |  | 发送给支付平台的订单号
order_id | int(11) |  |  | 业务订单号
order_type | varchar(5) |  |  | 支付订单类型
order_time | timestamp|  |  | 业务订单创建时间
order_title| varchar(128) |  | | 订单名称
payment_type | tinyint(1) |  |  | 支付类型
payment_status | tinyint(1) |  |  | 支付状态
payment_amount | bigint(11) |  |  | 支付金额
check_time | timestamp |  |  | 校验时间，每次校验更新
order_status | tinyint(1) |  |  | 订单状态 0.已履单， 1.未履单
product_id | varchar(50) |  | | 商品id
created_at | timestamp |  |  | 创建日期

order_type 支付订单类型
001：客户充值 002：用户体验

order_status 订单状态
0.已履单， 1.未履单


# Domain Report

## rpt_client_daily

客户新增日报表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
report_date | date |  | | 日期
trial_client_amount| int(11) | unsigned | | 体验用户总数
official_client_amount | int(11)| unsigned | | 正式用户总数



## rpt_customer_daily

用户新增日报表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | unsigned | auto_increment | 自增ID
report_date | date |  | | 日期
trial_customer_amount| int(11) | unsigned | | 体验用户总数
official_customer_amount | int(11)| unsigned | | 正式用户总数



## rpt_agent_port_daily

代理商端口销售日报表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
report_date | date |  | | 报表日期
agent_id| int(11) | un | | 代理商ID
agent_type | tinyint(1)| un | | 代理商类型(冗余字段)
level_one_id| int(11) | un | | 根代理商ID
parent_id | int(11) | un | | 父级代理商ID
port_amount | int(11) | un | | 分配端口数
port_amount_total | int(11) |un | | 下级代理商分配端口数总和
portpoint_amount| int(11) | un | | 分配端口点数
sale_port_amount | int(11) | | | 分配销量端口数
sale_portpoint_amount | int(11) | | | 分配销量端口点数
sub_port_amount| int(11) | un | | 下级代理商端口数总和
sub_portpoint_amount | int(11) | un | | 下级代理商点数总和

sub_port_amount 下级代理端口数总和（包含自己）
sub_portpoint_amount 下级代理商点数总和（包含自己）
port_amount_total 下级代理商分配端口数总和（包含自己）


## rpt_customer_token_daily_records

用户日活记录表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
report_date | date |  | | 报表日期
customer_id| int(11) | un | | 用户ID
client_id | int(11)| un | | 客户ID
client_customer_id| int(11) | un | | 客户用户唯一ID
customer_token | varchar(50) |  | | 用户token



## rpt_customer_token_daily


字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
report_date | date |  | | 报表日期
customer_uv| int(11) | un | | UV总数
customer_pv | tinyint(1)| un | | PV 总数


## rpt_client_records

客户操作记录表，包括新开体验客户，转正，体验删除操作

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
report_date | date |  | | 报表日期
record_type| tinyint(1) | un | | 记录类型
agent_id | int(11)| un | | 代理商ID
client_id| int(11) | un | | 客户ID
created_at | timestamp |  | | 创建时间
<font color="red">platform_id</font> | int(11) | | | admin后台登录用户

record_type 记录类型
1：新增体验客户 2： 转正客户 3： 删除客户
4: 锁定客户 5：解锁客户 6:体验客户过期 7:正式客户过期


## rpt_client_customer_relations

用户对应客户数量报表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
customer_id | int(11) | un | | 用户ID
trial_amount| int(11) | un | | 存在于体验客户数量
official_amount | int(11)| un | | 存在于正式客户数量
customer_trial_amount| int(11) | un | | 存在于一元体验客户数量
customer_official_amount | int(11) | un | | 存在于一元正式客户数量
total_trial_amount| int(11) | un | | 存在于体验客户总数
total_official_amount | int(11)| un | | 存在于正式客户总数
total_customer_trial_amount| int(11) | un | | 存在于一元体验客户总数
total_customer_official_amount | int(11) | un | | 存在于一元正式客户总数



## rpt_customer_content_daily

用户每日学习情况日报表

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
report_date | date |  | | 报表日期
client_id| int(11) | un | | 客户ID
customer_id | int(11)|  | | 用户ID
customer_name| varchar(50) |  | | 用户名（冗余）
client_customer_id | int(11) |  | | 客户用户关系ID
department_id| int(11) |  | | 部门ID
reading_time | bigint()|  | | 阅读时长
learning_point| int(11) |  | | 学习力


## rpt_customer_content_read_daily

书课阅读量明细表（每日）

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
report_date | datetime |  | | 报表日期
client_customer_id| int(11) | un | | 企业用户关系ID
customer_id | int(11)|  | | 用户ID
customer_name| varchar(50) |  | | 用户名（冗余）
client_id | int(11) |  | | 所属客户ID
content_class| tinyint(1) |  | | 内容型别
pack_id | int(11)|  | | 课程ID
pack_title| varchar(200) |  | | 课程标题（冗余）
content_id | int(11) |  | | 内容ID
content_title| varchar(200) |  | | 内容标题（冗余）
reading_duration | int(11)|  | | 阅读时长
reading_amount| int(11) |  | | 阅读次数

content_class 内容型别
0 : 普通内容
1：课程内容



## rpt_customer_content_record_daily

用户每日阅读详情报表，即 个人学习记录明细表
导出自 clt_customer_content_records ，clt_customer_assignment_records 只记录获得学习力的记录

字段 | 类型 | Extra | 默认 | 备注
---------- | ---------- | ---------- | ---------- | ----------
id         | int(11) | un | auto_increment | 自增ID
client_custome_id| int(11) | un | | 企业用户关系ID
customer_id | int(11)|  | | 用户ID
customer_name| varchar(50) |  | | 用户名（冗余）
client_id | int(11) |  | | 所属客户ID
content_id | int(11) |  | | 内容ID
content_title| varchar(200) |  | | 内容标题
reading_date| date |  | | 阅读日期
reading_time | timestamp |  | | 阅读开始时间（客户端）
reading_duration | int(11)|  | | 本内容阅读时长
learning_point| int(11) |  | | 学习力
content_type | tinyint(1) |  | | 内容类型
content_type_title | varchar(50) |  | | 学习方式
source_id | int(11) | un | | 来源基础数据id

content_type:  1 为视频 2为音频 3为做作业
