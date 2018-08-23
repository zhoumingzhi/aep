# acct.bill.list

## 概述

5.8.3 月度账户查询

## 更新历史

 - [20180115 zhoumingzhi] 创建本文档。

## 接口规范要求

指定客户custID查询月度账单。

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|custID|Long|必填|ID|
|2|payStatus|String|必选|支付状态 0:未结清账单，1:部分结清账单,2:全部结清账单,3:返销接口 ""：空值代表全部|
|3|billCycle|String|可选|账期|
|4| page | int| 是|分页|
|5| pageSize | int| 是|分页大小|



## 输出结果
| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|retCode|String|必填|0 表示成功，其他值则为错误代码|
|2|msg|String|可选|提示信息|
|3|count|int|可选|总共记录数|
|4|billInfo|Array|必填|账单信息|

*其中账单billInfo格式为

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|Id|Long|必填|记录主键ID|
|2|acctID|Long|必填|账户ID|
|3|custID|Long|必填|客户ID|
|4|custName|Long|必填||
|5|payStatus|String|必填|支付状态|
|6|billCycle|String|必填|账期|
|7|acctItemName|Long|必填|费用名称|
|8|amt|Long|必填|应付金额（含税）|
|9|unPaidAmt|Long|必填|欠费金额|
|10|paidAmt|Long|必填|已缴金额|

## 异常
 * 返回相应的信息，并返回代码：
 
## 样例

下面是一个样例，
```
Enterprise/CustomerMag/AccountBillInfoQuery
```

```
按照客户custID查找
输入参数
{
	"data": {
		"custID": "111",
		"payStatus": "0",
		"pageSize": "5",
        "page":"1",
		"billCycle": "201811"
	}	
}
输出结果：
{
	"msg": "服务调用成功",
	"retCode": "0",
	"count": 3 ,
	"billInfo": [{
		"unwoffAMT": "0",
		"payStatus ": "未缴费",
		"acctItemName ": "dming",
		"acctID": "222",
		"amt": "23",
		"billCycle": "201811"
	},
	{
		"unwoffAMT": "32",
		"payStatus ": "已缴费",
		"acctItemName ": null,
		"acctID": "211",
		"amt": "34",
		"billCycle": "201811"
	},
	{
		"unwoffAMT": "211",
		"payStatus ": "未缴费",
		"acctItemName ": "zhou",
		"acctID": "211",
		"amt": "234",
		"billCycle": "201811"
	}]
}
```


