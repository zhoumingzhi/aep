# typeTenantId

## 概述

判断客户类型

## 更新历史

 - [20170906 raoduan] 创建本文档。
## 接口规范要求
创建订单

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|custID|Long|必填|客户ID|

## 输出结果
| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|RetCode|String|必填|0 表示成功，其他值则为错误代码|
|2|Msg|String|可选|提示信息|
|3|type|String|必填|aep:内部收费,crm:外部收费|



## 异常
 * 返回相应的信息，并返回代码：core.ok
 
## 样例


