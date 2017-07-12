# 接口设计

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

* http响应码 200 服务端响应成功

* http响应码 4xx 或者 5xx，格式：

```
{
    "code": "REQUIRE_ARGUMENT",
    "message": "错误消息",
    "detial": "报错详情"
}
```

#### 统一响应

#### 结构约定

* ## 基础功能接口

## 



