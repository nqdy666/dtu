# 数据库表设计

id 默认自增

* 用户表（user）

| 字段 | 数据类型 | 主键 | 是否不为空 | 独一无二 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| id | INT\(11\) | 是 | 是 |  |  | ID |
| login\_name | VARCHAR\(45\) |  |  | 是 |  | 登录名 |
| nick\_name | VARCHAR\(80\) |  |  |  |  | 昵称 |
| password | VARCHAR\(32\) |  |  |  |  | 密码 |
| create\_time | TIMESTAMP |  | 是 |  | CURRENT\_TIMESTAMP ON UPDATE CURRENT\_TIMESTAMP | 创建时间 |
| update\_time | TIMESTAMP |  | 是 |  | CURRENT\_TIMESTAMP ON UPDATE CURRENT\_TIMESTAMP | 更新时间 |

* 工厂（factory）

| 字段 | 数据类型 | 主键 | 是否不为空 | 独一无二 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| id | INT\(11\) | 是 | 是 |  |  | ID |
| name | VARCHAR\(45\) |  |  | 是 |  | 工厂名 |
| create\_time | TIMESTAMP |  | 是 |  | CURRENT\_TIMESTAMP ON UPDATE CURRENT\_TIMESTAMP | 创建时间 |
| update\_time | TIMESTAMP |  | 是 |  | CURRENT\_TIMESTAMP ON UPDATE CURRENT\_TIMESTAMP | 更新时间 |

* 总闸（main\_switch）

| 字段 | 数据类型 | 主键 | 是否不为空 | 独一无二 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| id | INT\(11\) | 是 | 是 |  |  | ID |
| factory\_id | INT\(11\) |  | 是 | 是 |  | 工厂ID |
| name | VARCHAR\(45\) |  |  |  |  | 总闸名称 |
| status | INT\(11\) |  | 是 |  | 2 | 1开，2关 |
| create\_time | TIMESTAMP |  | 是 |  | CURRENT\_TIMESTAMP ON UPDATE CURRENT\_TIMESTAMP | 创建时间 |
| update\_time | TIMESTAMP |  | 是 |  | CURRENT\_TIMESTAMP ON UPDATE CURRENT\_TIMESTAMP | 更新时间 |



* 设备表（device）

| 字段 | 数据类型 | 主键 | 是否不为空 | 独一无二 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| id | INT\(11\) | 是 | 是 |  |  | ID |
| name | VARCHAR\(80\) |  |  |  |  | 设备名称 |
| no | VARCHAR\(45\) |  | 是 | 是 |  | 设备编号 |
| status | INT\(11\) |  | 是 |  |  | 设备状态 |
| create\_time | TIMESTAMP |  | 是 |  | CURRENT\_TIMESTAMP ON UPDATE CURRENT\_TIMESTAMP | 创建时间 |
| update\_time | TIMESTAMP |  | 是 |  | CURRENT\_TIMESTAMP ON UPDATE CURRENT\_TIMESTAMP | 更新时间 |

* 设备日志表（device\_log）

| 字段 | 数据类型 | 主键 | 是否不为空 | 独一无二 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| id | INT\(11\) | 是 | 是 |  |  | ID |
| device\_id | INT\(11\) |  | 是 |  |  | 设备ID |
| status | INT\(11\) |  | 是 |  |  | 设备状态 |
| mark | VARCHAR\(240\) |  |  |  |  | 备注 |
| create\_time | TIMESTAMP |  | 是 |  | CURRENT\_TIMESTAMP ON UPDATE CURRENT\_TIMESTAMP | 创建时间 |



