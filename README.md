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

* 设备表（device）
* 设备日志表（device\_log）
* 


