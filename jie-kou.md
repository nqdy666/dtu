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

* ##### **USER**

```
{
    "id": 1,
    "loginName": "root",
    "nickName": "超级管理员",
    "createTime": 1499847783000,
    "updateTime": 1499847783000
}
```

* ##### DEVICE

```
{
    "id": 3,
    "name": "设备名称",
    "no": "12312323",
    "status": 2,
    "createTime": 1498044412000,
    "updateTime": 1498044412000
}
```

* ##### DEVICE\_LOG

```
{
    "id": 3,
    "deviceId": 3,
    "status": 2,
    "mark": '',
    "createTime": 1499852542000
}
```

## 基础功能接口

### 用户相关

#### 获取单个用户信息\[GET\] /m/user/{user\_id}

* 请求内容：

```
{
    "id": 3,
    "loginName": "root",
    "nickName": "超级管理员",
    "createTime": 1497966418000,
    "updateTime": 1497966418000
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

