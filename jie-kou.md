# 接口设计

## 摘要

## 概述

#### **服务端地址**

* 接口使用 REST 规范，传入参数及传出参数都以标准 JSON 编码
* 接口地址 接口版本为v0.1

  * 生产：待定

#### 请共通头部定义

* Accept: application/json
* Content-Type: application/json

#### 国际化

待定

#### 错误码

常用的几个错误类型

| HTTPCODE | CODE | MESSAGE |
| :--- | :--- | :--- |
| 400 | DTU/BAD\_REQUEST | 无效请求 |
| 400 | DTU/REQUIRE\_ARGUMENT | 缺少参数 |
| 400 | DTU/INVALID\_ARGUMENT | 无效参数\(格式不对,长度过长或过短等\) |
| 400 | DTU/REPEAT\_ARGUMENT | 重复参数 |
| 401 | DTU/UNAUTHORIZED | 未授权\(默认\) |
| 403 | DTU/AUTH\_DENIED | 授权受限（无权限或IP地址受限等） |
| 403 | DTU/ACCESS\_DENIED | 不允许访问 |
| 500 | DTU/INTERNAL\_SERVER\_ERROR | 服务器错误 |
| 404 | DTU/USER\_NOT\_FOUND | 用户找不到 |
| 409 | DTU/USER\_EXISTS | 用户已存在 |
| 400 | DTU/USER\_PASSWORD\_SAME | 用户新旧密码一样 |
| 400 | DTU/USER\_OLD\_PASSWORD\_INCORRECT | 旧密码不正确 |
| 404 | DTU/DEVICE\_NOT\_FOUND | 设备找不到 |
| 409 | DTU/DEVICE\_EXISTS | 设备已存在 |
| 404 | DTU/DEVICE\_LOG\_NOT\_FOUND | 设备日志找不到 |

#### 统一响应

http响应码 200 服务端响应成功

* http响应码 4xx 或者 5xx，格式：

```
{
    "code": "REQUIRE_ARGUMENT",
    "message": "错误消息",
    "detial": "报错详情"
}
```

#### 结构约定

* ##### USER

```
{
    "id": 1,
    "login_name": "root",
    "nick_name": "超级管理员",
    "create_time": 1499847783000,
    "update_time": 1499847783000
}
```

* ##### FACTORY

```
{
    "id": 1,
    "name": "工厂名称",
    "create_time": 1499847783000,
    "update_time": 1499847783000
}
```

* ##### MAIN\_SWITCH

```
{
    "id": 1,
    "factory_id": "1",
    "name": "总闸名称",
    "switch_status": 2,
    "abnormal_status": 1,
    "create_time": 1499847783000,
    "update_time": 1499847783000
}
```

* ##### PLC

```
{
    "id": 1,
    "factory_id": "1",
    "name": "PLC设备名称",
    "switch_status": 2,
    "abnormal_status": 1,
    "create_time": 1499847783000,
    "update_time": 1499847783000
}
```

* ##### ECE

```
{
    "id": 1,
    "plc_id": "1",
    "name": "环境设备名称",
    "no": "设备编码",
    "switch_status": 2,
    "abnormal_status": 1,
    "create_time": 1499847783000,
    "update_time": 1499847783000
}
```

* ##### POOL

```
{
    "id": 1,
    "factory_id": "1",
    "name": "池子名称",
    "no": "池子编码",
    "switch_status": 2,
    "abnormal_status": 1,
    "create_time": 1499847783000,
    "update_time": 1499847783000
}
```

* ##### DO\_SENSOR

```
{
    "id": 1,
    "factory_id": "1",
    "name": "溶解氧传感器名称",
    "no": "设备编码",
    "switch_status": 2,
    "abnormal_status": 1,
    "value": "溶解氧值",
    "create_time": 1499847783000,
    "update_time": 1499847783000
}
```

* ##### WATER\_SENSOR

```
{
    "id": 1,
    "factory_id": "1",
    "name": "名称",
    "no": "设备编码",
    "switch_status": 2,
    "abnormal_status": 1,
    "value": "溶解氧值",
    "create_time": 1499847783000,
    "update_time": 1499847783000
}
```

* ##### BIG\_FLOW\_METER

```
{
    "id": 1,
    "factory_id": "1",
    "name": "名称",
    "no": "设备编码",
    "switch_status": 2,
    "abnormal_status": 1,
    "value": "流量值",
    "create_time": 1499847783000,
    "update_time": 1499847783000
}
```

* ##### DTU

```
{
    "id": 1,
    "factory_id": "1",
    "name": "名称",
    "url": "设备URL",
    "create_time": 1499847783000,
    "update_time": 1499847783000
}
```

* ##### DEVICE\_LOG

```
{
    "id": 3,
    "device_type": 3,
    "device_id": 3,
    "switch_status": 2,
    "abnormal_status": 1,
    "value_one": "1",
    "value_two": "2",
    "operator_id": 1,
    "mark": '备注',
    "create_time": 1499852542000
}
```

* ##### USER\_LOG

```
{
    "id": 1,
    "user_id": "1",
    "mark": '备注',
    "create_time": 1499852542000
}
```

* ##### SMS\_TEMPLATE

```
{
    "id": 1,
    "title": "标题",
    "receivers": '13452331156,18456112256',
    "template": "模板",
    "mark": '备注',
    "create_time": 1499847783000,
    "update_time": 1499847783000
}
```

## 基础功能接口

### 用户相关

#### 获取单个用户信息\[GET\] /m/user/{user\_id}

* 请求内容：

```
{
    "id": 3,
    "login_name": "root",
    "nick_name": "超级管理员",
    "create_time": 1497966418000,
    "update_time": 1497966418000
}
```

* 响应内容：

[USER](#user)

* 错误码：

DTU/USER\_NOT\_FOUND

#### 获取用户列表\[GET\] /m/users?$count=true&$offset=偏移量&$limit=数量

* 响应内容：

```
{
    "count":1,
    "items":[
      {USER},...
    ]
}
```

#### 创建用户\[POST\] /m/users

请求内容：

```
{
    "login_name": "admin1",
    "nick_name": "admin",
    "password": "E10ADC3949BA59ABBE56E057F20F883E"
}
```

* 响应内容：

[USER](#user)

* 错误码：

DTU/USER\_EXISTS

#### 更新用户信息\[PATCH\] /m/users/{user\_id}

* 响应内容：[USER](https://www.gitbook.com/book/nqdy666/dtu/edit#)

* 错误码：

DTU/USER\_NOT\_FOUND

#### 删除用户\[DELETE\] /m/users/{user\_id}

* 错误码：

DTU/USER\_NOT\_FOUND

#### 修改用户密码\[PUT\] /m/users/{user\_id}/password

* 错误码：

DTU/USER\_PASSWORD\_SAME

DTU/USER\_OLD\_PASSWORD\_INCORRECT

#### 重置用户密码\[PUT\] /m/users/{user\_id}/password/reset

### 工厂相关

#### 获取工厂信息\[GET\] /m/factories/{factory\_id}

#### 获取工厂列表\[GET\] /m/factories?$count=true&$offset=偏移量&$limit=数量

#### 添加工厂\[POST\] /m/factories

#### 更新工厂信息\[PATCH\] /m/factories/{factory\_id}

#### 删除工厂\[DELETE\] /m/factories/{factory\_id}

### DTU设备相关

#### 获取某一个工厂下DTU设备信息\[GET\] /m/factories/{factory\_id}/dtu

#### 添加DTU设备\[POST\] /m/dtues

#### 更新DTU设备信息\[PATCH\] /m/dtues/{dtu\_id}

#### 删除DTU设备\[DELETE\] /m/dtues/{dtu\_id}

### 总闸相关

#### 获取某一个工厂下总闸信息\[GET\] /m/factories/{factory\_id}/main\_switch

#### 添加总闸\[POST\] /m/main\_switches

#### 更新总闸信息\[PATCH\] /m/main\_switches/{main\_switch\_id}

#### 删除总闸\[DELETE\] /m/main\_switches/{main\_switch\_id}

### PLC设备相关

#### 获取某一个工厂下PLC设备信息\[GET\] /m/factories/{factory\_id}/plc

#### 添加PLC设备\[POST\] /m/plcs

#### 更新PLC设备信息\[PATCH\] /m/plcs/{plc\_id}

#### 删除PLC设备\[DELETE\] /m/plcs/{plc\_id}

### 环境控制设备相关

#### 获取某一个PLC设备下环境控制设备列表\[GET\] /m/plcs/{plc\_id}/eces?$count=true&$offset=偏移量&$limit=数量

#### 获取环境控制设备列表\[GET\] /m/eces?$count=true&$offset=偏移量&$limit=数量&no=设备编码

#### 获取环境控制设备信息\[GET\] /m/eces/{ece\_id}

#### 添加环境控制设备\[POST\] /m/eces 

#### 更新环境控制设备\[PATCH\] /m/eces/{ece\_id}

#### 删除环境控制设备\[DELETE\] /m/eces/{ece\_id}

### 池子相关

#### 获取某一个工厂下池子列表\[GET\] /m/factories/{factory\_id}/pools?$count=true&$offset=偏移量&$limit=数量

#### 获取池子列表\[GET\] /m/pools?$count=true&$offset=偏移量&$limit=数量&no=池子编码

#### 获取池子信息\[GET\] /m/pools/{pool\_id}

#### 添加池子\[POST\] /m/pools 

#### 更新池子\[PATCH\] /m/pools/{pool\_id}

#### 删除池子\[DELETE\] /m/pools/{pool\_id}

### 溶解氧传感器相关

#### 获取某一个工厂下溶解氧传感器列表\[GET\] /m/factories/{factory\_id}/do\_sensors?$count=true&$offset=偏移量&$limit=数量

#### 获取溶解氧传感器列表\[GET\] /m/do\_sensors?$count=true&$offset=偏移量&$limit=数量&no=传感器编码

#### 获取溶解氧传感器信息\[GET\] /m/do\_sensors/{do\_sensor\_id}

#### 添加溶解氧传感器\[POST\] /m/do\_sensors 

#### 更新溶解氧传感器\[PATCH\] /m/do\_sensors/{do\_sensor\_id}

#### 删除溶解氧传感器\[DELETE\] /m/do\_sensors/{do\_sensor\_id}

### 污水传感器相关

#### 获取某一个工厂下污水传感器列表\[GET\] /m/factories/{factory\_id}/water\_sensors?$count=true&$offset=偏移量&$limit=数量

#### 获取污水传感器列表\[GET\] /m/water\_sensors?$count=true&$offset=偏移量&$limit=数量&no=传感器编码

#### 获取污水传感器信息\[GET\] /m/water\_sensors/{water\_sensor\_id}

#### 添加污水传感器\[POST\] /m/water\_sensors 

#### 更新污水传感器\[PATCH\] /m/water\_sensors/{water\_sensor\_id}

#### 删除污水传感器\[DELETE\] /m/water\_sensors/{water\_sensor\_id}

### 大流量表相关

#### 获取某一个工厂下大流量表列表\[GET\] /m/factories/{factory\_id}/big\_flow\_meters?$count=true&$offset=偏移量&$limit=数量

#### 获取大流量表列表\[GET\] /m/big\_flow\_meters?$count=true&$offset=偏移量&$limit=数量&no=传感器编码

#### 获取大流量表信息\[GET\] /m/big\_flow\_meters/{big\_flow\_meter\_id}

#### 添加大流量表\[POST\] /m/big\_flow\_meters

#### 更新大流量表\[PATCH\] /m/big\_flow\_meters/{big\_flow\_meter\_id}

#### 删除大流量表\[DELETE\] /m/big\_flow\_meters/{big\_flow\_meter\_id}

### 设备日志相关

#### 获取设备日志列表\[GET\] /m/device\_logs?$count=true&$offset=偏移量&$limit=数量&device\_type=设备类型&device\_id=设备ID

#### 获取设备日志信息\[GET\] /m/device\_logs/{device\_logs_id}

#### 获取设备日志信息\[GET\] /m/device\_logs/{device\_logs_id}

#### 添加设备日志\[POST\] /m/device\_logs

### 设备相关

#### 获取单个设备信息\[GET\] /m/devices/{device\_id}

* 错误码：

DTU/DEVICE\_NOT\_FOUND

#### 获取设备列表\[GET\] /m/devices?$count=true&$offset=偏移量&$limit=数量

#### 添加设备\[POST\] /m/devices

* 错误码：

DTU/DEVICE\_EXISTS

#### 更新设备\[PATCH\] /m/devices/{device\_id}

* 错误码：

DTU/DEVICE\_NOT\_FOUND

#### 删除设备\[DELETE\] /m/devices/{device\_id}

* #### 错误码：

DTU/DEVICE\_NOT\_FOUND

### 设备操作日志相关

#### 获取某一个设备的操作日志\[GET\] /m/devices/{device\_id}/logs?$count=true&$offset=偏移量&$limit=数量

#### 获取某一条设备操作日志详情\[GET\] /m/devices/logs/{device\_log\_id}

* 错误码：

DTU/DEVICE\_LOG\_NOT\_FOUND

#### 删除某一条设备操作日志\[GET\] /m/devices/logs/{device\_log\_id}

* #### 错误码：

DTU/DEVICE\_LOG\_NOT\_FOUND

#### 添加设备的操作日志\[GET\] /m/devices/{device\_id}/logs

* #### 错误码：

DTU/DEVICE\_NOT\_FOUND

