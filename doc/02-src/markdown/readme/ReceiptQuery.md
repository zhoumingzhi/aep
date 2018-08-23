# receipt.info.list

## 概述

5.10.6 查询发票信息
对应的数据表为CM_RET_INFO

## 更新历史

 - [20180115 zhoumingzhi] 创建本文档。
## 接口规范要求

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|custID|Long|必填|客户ID|
|2| page | int| 是|分页|
|3| pageSize | int| 是|分页大小|

## 输出结果
| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|retCode|String|必填|0 表示成功，其他值则为错误代码|
|2|msg|String|可选|提示信息|
|3|count|Int|必选|总共的记录个数|
|4|receiptInformation|Array|必选|发票记录|

其中 receiptInformation 格式为：
| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|custID|Long|必填|客户ID|
|2|ID|Long|必填|主键ID|
|3|openType|Int|必填|开具类型|
|4|receiptTitle|String|必填|发票抬头|
|5|receiptType|Int|必填|发票类型|
|6|taxRstNum|String|可选|税务登记证号|
|7|bankName|String|可选|基本开户银行名称|
|8|bankAccount|String|可选|基本开户账号|
|9|address|String|可选|注册场所地址|
|10|phone|String|可选|注册固定电话|

## 异常
 * 返回相应的信息，并返回代码：
 
## 样例

服务地址如下
```
Enterprise/AcctMag/Receipt/ReceiptQuery
```

```
输入参数
{
	"data": {
		"custID": "111"
	}
}
输出结果：
{
	"msg": "服务调用成功",
	"retCode": "0",
	"count": 1,
	"receiptInformation": [{
	{
		"receiptTitle": "hahha",
		"bankName": "dege",
		"openType": "2",
		"receiptType": 2,
		"taxRstNum": "zhoumingzhi",
		"address": "deg",
		"custID": "111",
		"ID": "315176333946944656",
		"phone": "123",
		"bankAccount": "xd"
	}]
}
```