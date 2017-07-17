
---

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

* PLC（plc）

| 字段 | 数据类型 | 主键 | 是否不为空 | 独一无二 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| id | INT\(11\) | 是 | 是 |  |  | ID |
| factory\_id | INT\(11\) |  | 是 | 是 |  | 工厂ID |
| name | VARCHAR\(45\) |  |  |  |  | PLC设备名称 |
| status | INT\(11\) |  | 是 |  | 2 | 1开，2关 |
| create\_time | TIMESTAMP |  | 是 |  | CURRENT\_TIMESTAMP ON UPDATE CURRENT\_TIMESTAMP | 创建时间 |
| update\_time | TIMESTAMP |  | 是 |  | CURRENT\_TIMESTAMP ON UPDATE CURRENT\_TIMESTAMP | 更新时间 |

* 控制环境设备environmental control equipment（ece）

| 字段 | 数据类型 | 主键 | 是否不为空 | 独一无二 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| id | INT\(11\) | 是 | 是 |  |  | ID |
| plc\_id | INT\(11\) |  | 是 | 与name联合唯一索引 |  | PLC设备ID |
| name | VARCHAR\(45\) |  | 是 | 与plc\_id联合唯一索引 |  | 环境设备名称 |
| no | VARCHAR\(45\) |  | 是 | 是 |  | 设备编码 |
| status | INT\(11\) |  | 是 |  | 2 | 1开，2关 |
| create\_time | TIMESTAMP |  | 是 |  | CURRENT\_TIMESTAMP ON UPDATE CURRENT\_TIMESTAMP | 创建时间 |
| update\_time | TIMESTAMP |  | 是 |  | CURRENT\_TIMESTAMP ON UPDATE CURRENT\_TIMESTAMP | 更新时间 |

* 池子（pool）

| 字段 | 数据类型 | 主键 | 是否不为空 | 独一无二 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| id | INT\(11\) | 是 | 是 |  |  | ID |
| factory\_id | INT\(11\) |  | 是 | 是 |  | 工厂ID |
| no | VARCHAR\(45\) |  | 是 | 是 |  | 池子编码 |
| name | VARCHAR\(45\) |  |  |  |  | 池子名称 |
| status | INT\(11\) |  | 是 |  | 2 | 1开，2关 |
| create\_time | TIMESTAMP |  | 是 |  | CURRENT\_TIMESTAMP ON UPDATE CURRENT\_TIMESTAMP | 创建时间 |
| update\_time | TIMESTAMP |  | 是 |  | CURRENT\_TIMESTAMP ON UPDATE CURRENT\_TIMESTAMP | 更新时间 |

* 溶解氧传感器dissolved oxygen sensor（do\_sensor）

| 字段 | 数据类型 | 主键 | 是否不为空 | 独一无二 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| id | INT\(11\) | 是 | 是 |  |  | ID |
| factory\_id | INT\(11\) |  | 是 | 是 |  | 工厂ID |
| name | VARCHAR\(45\) |  |  |  |  | PLC设备名称 |
| no | VARCHAR\(45\) |  | 是 | 是 |  | 设备编码 |
| status | INT\(11\) |  | 是 |  | 2 | 1开，2关 |
| value | VARCHAR\(60\) |  |  |  |  | 溶解氧值 |
| create\_time | TIMESTAMP |  | 是 |  | CURRENT\_TIMESTAMP ON UPDATE CURRENT\_TIMESTAMP | 创建时间 |
| update\_time | TIMESTAMP |  | 是 |  | CURRENT\_TIMESTAMP ON UPDATE CURRENT\_TIMESTAMP | 更新时间 |

* 污水传感器water sensor（water\_sensor）

| 字段 | 数据类型 | 主键 | 是否不为空 | 独一无二 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| id | INT\(11\) | 是 | 是 |  |  | ID |
| factory\_id | INT\(11\) |  | 是 | 是 |  | 工厂ID |
| name | VARCHAR\(45\) |  |  |  |  | PLC设备名称 |
| no | VARCHAR\(45\) |  | 是 | 是 |  | 设备编码 |
| status | INT\(11\) |  | 是 |  | 2 | 1开，2关 |
| value | VARCHAR\(60\) |  |  |  |  | 溶解氧值 |
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



