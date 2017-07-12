# 数据库表设计

* 用户表（user）

| 字段 | 数据类型 | 主键 | 是否不为空 | 独一无二 | 默认值 | 说明 |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| id | INT\(11\) | 是 | 是 |  |  |  |
| login\_name | VARCHAR\(45\) |  |  | 是 |  |  |
| nick\_name | VARCHAR\(80\) |  |  |  |  |  |
| password | VARCHAR\(32\) |  |  |  |  |  |
| create\_time | TIMESTAMP |  | 是 |  |  |  |
| update\_time | TIMESTAMP |  | 是 |  |  |  |

* 设备表（device）
* 设备日志表（device\_log）
* 


