# receipt.create

## 概述

5.10.3 创建发票信息
对应的数据表示CM_RET_INFO

## 更新历史

 - [20180115 zhoumingzhi] 创建本文档。

## 接口规范要求

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|custID|Long|必填|客户ID|
|2|openType|Int|必填|开具类型 1:增值税普通发票,2:增值税专用发票|
|3|receiptTitle|String|必填|发票抬头|
|4|receiptType|Int|必填|发票类型|
|5|taxRstNum|String|可选|税务登记证号|
|6|bankName|String|可选|基本开户银行名称|
|7|bankAccount|String|可选|基本开户账号|
|8|address|String|可选|注册场所地址|
|9|phone|String|可选|注册固定电话|

## 输出结果

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|retCode|String|必填|0 表示成功，其他值则为错误代码|
|2|msg|String|可选|提示信息|
|3|custID|Long|必填|客户ID|
|4|ID|Long|必填|主键ID|


## 异常
 * 返回相应的信息，并返回代码：
 
## 样例

下面是一个样例，
服务地址如下；参数参考下面CCR格式
```
Enterprise/AcctMag/Receipt/ReceiptCreate
```

```
输入参数
{
	"data": {
		"bankAccount": "xd",
		"address": "deg",
		"receiptType": "2",
		"receiptTitle": "hahha",
		"phone": "123",
		"custID": "111",
		"taxRstNum": "zhoumingzhi",
		"bankName": "dege",
		"openType": "2"
	}
}
输出结果：
{
	"msg": "服务调用成功",
	"custID": "111",
	"ID": "315176333946944656",
	"retCode": "0"
}
```