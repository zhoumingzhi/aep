# receipt.get.list

## 概述
5.10.12 发票索取列表查询
对应的数据表为IB_RET_REQ
## 更新历史

 - [20180115 zhoumingzhi] 创建本文档。

## 接口规范要求

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|custID|Long|必填|客户ID|
|2|isMonthly|int|必填|是否按月1:是 0：否|
|3|month|String|可选|当是否按月选择“是”，需选择月份，格式YYYYMM|
|4|startTime|Datetime|可选|当是否按月选择“否”，开始日期|
|5|endTime|Datetime|可选|当是否按月选择“否”，截止日期|
|6| page | int| 是|分页|
|7| pageSize | int| 是|分页大小|


## 输出结果

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|retCode|String|必填|0 表示成功，其他值则为错误代码|
|2|msg|String|可选|提示信息|
|3|custID|Long|必填|客户ID|
|4|count|int|必填|查询记录总个数|
|5|receiptGetListInfo|Array|可选|发票索取列表信息|

其中发票索取列表信息receiptGetListInfo为：

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|ID|String|必填|发票索取主键|
|2|orderID|String|必填|订单编号|
|3|productName|String|必填|产品名称|
|4|orderType|int|必填|订单类型|
|5|payTime|Datetime|必填|订单支付时间|
|6|amt|Float|必填|订单金额|
|7|receiptAMT|Float|必填|可开票金额|

## 异常
 * 返回相应的信息，并返回代码：
 
## 样例

下面是一个样例，
服务地址如下；参数参考下面格式
```
Enterprise/AcctMag/Receipt/ReceiptGetListQuery
```

```
输入参数按照月份
{
	"data": {
		"month": "201801",
		"isMonthly": "1",
		"custID": "111"
	}	
}
输出结果：
{
	"msg": "服务调用成功",
	"custID": "111",
	"retCode": "0",
	"count": 2,
	"receiptGetListInfo": [{
		"orderType": "3234",
		"amt": "23223",
		"receiptAMT": "234",
		"orderID": "322",
		"payTime": "2018-01-18 14:19:24.0",
		"productName": "zdfe"
	},
	{
		"orderType": "334",
		"amt": "324",
		"receiptAMT": "234",
		"orderID": "323",
		"payTime": "2018-01-03 17:28:50.0",
		"productName": "daf"
	}]
}
输入参数按照日期
{
	"data": {
		"isMonthly": "0",
		"custID": "111",
		"startTime": "20180101",
		"endTime": "20180301"
	}
}
输出结果：
{
	"msg": "服务调用成功",
	"retCode": "0",
	"custID": "111",
	"count": 3,
	"receiptGetListInfo": [{
		"orderType": "3234",
		"amt": "23223",
		"receiptAMT": "234",
		"orderID": "322",
		"payTime": "2018-01-18 14:19:24.0",
		"productName": "zdfe"
	},
	{
		"orderType": "334",
		"amt": "324",
		"receiptAMT": "234",
		"orderID": "323",
		"payTime": "2018-01-03 17:28:50.0",
		"productName": "daf"
	},
	{
		"orderType": "3",
		"amt": "234",
		"receiptAMT": "23",
		"orderID": "233",
		"payTime": "2018-02-13 16:38:09.0",
		"productName": "322"
	}]
}
```