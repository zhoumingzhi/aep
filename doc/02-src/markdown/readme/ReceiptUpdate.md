# receipt.update

## 概述

5.10.4 修改发票信息
对应的数据表为CM_RET_INFO

## 更新历史

 - [20180115 zhoumingzhi] 创建本文档。

## 接口规范要求

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|ID|Long|必填|主键ID|
|2|openType|Int|必填|开具类型|
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
|3|ID|Long|必填|主键ID|
|4|custID|Long|必填|客户ID|


## 异常
 * 返回相应的信息，并返回代码：
 
## 样例

下面是一个样例，
服务地址如下
```
Enterprise/AcctMag/Receipt/ReceiptUpdate
```

```
输入参数
{
	"data": {
		"ID":"315176333946944656",
		"bankAccount": "xd",
		"address": "deg",
		"receiptType": "2",
		"receiptTitle": "hahha",
		"phone": "xd",
		"custID": "111",
		"taxRstNum": "zhdgoumingzhi",
		"bankName": "dege",
		"openType": "2"
	}
}
输出结果：
{
	"msg": "服务调用成功",
	"ID": "315176333946944656",
	"custID": "111",
	"retCode": "0"
}
```