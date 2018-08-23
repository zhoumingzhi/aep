# cust.status.update

## 概述

5.8.5 修改客户状态

## 更新历史
 - [20180115 zhoumingzhi] 创建本文档

## 接口规范要求

## 输入参数


| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
| 1 | custID | Long| 是| 账户信息|
| 1 | oriStatus | String| 是| 客户原始状态|
| 3 | updateStatus | String| 是| 客户更新后的状态|

## 输出结果

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|retcode|String|必填|0表示成功，其他值表示错误代码|
|2|msg|String|可选|提示信息|
|3|custID|String|必选|客户账户|
|4|ID|String|必选|主键ID|

## 异常
 * 返回相应的信息，并返回代码：core.ok
 
## 样例

下面是一个样例，
```
Enterprise/CustomerMag/UpdateCustStatus
```
```
输入参数
{
	"data": {
		"updateStatus": "2",
		"custID": "111",
		"oriStatus": "1"
	},    
}

输出结果
{
	"msg": "服务调用成功",
	"custID": "111",
	"ID": "315178264450358705",
	"retCode": "0"
}
```


