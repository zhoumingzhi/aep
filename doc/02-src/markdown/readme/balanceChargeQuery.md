balanceCharge.query

## 概述

## 更新历史

 - [20170906 raoduan] 创建本文档。

## 接口规范要求

充值历史查询

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|tenantId|Long|必填|租户ID,不传就标识查询全部|
|2|state|Long|必填|支付状态 state = 1 为下单，=2 已支付 全部不传|
|3|chargeType|Long|必填|充值渠道 = 1 翼支付，=1 汇款底单 全部不传|
|4|startTime|string|必填|查询起始时间| 
|5|endTime|String|必填|查询失效时间| 
|6|page|Long|必填|查询页数| 
|7|pageSize|long|必填|一页个数|

## 输出结果

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|retCode|String|必填|0 表示成功，其他值则为错误代码|
|2|msg|String|可选|提示信息|
|3|count|int|必填|符合条件个数|
|4|info|ArrayList|必填||

其中`info`为

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|Id|String|必填|主键ID|
|2|custId|String|必填|客户Id|
|3|custName|String|必填|客户姓名|
|4|state|Long|必填|支付状态 =1，已下单，但还未支付；=2，成功支付；=3，支付超时，订单关闭；=4 支付失败，订单关闭 =5 已经退款|
|5|chargeType|String|必填|chargeType = 1 表示翼支付单充值，=2 表示汇款底单充值|
|6|tradeAmt|long|必填|下单金额|
|7|payAmt|long|必填|支付金额|
|8|reFundAmt|long|必填|可退金额|
|9|payTime|String|必填|支付时间|

## 异常

 * 返回相应的信息，并返回代码：core.ok
 
## 样例

下面是一个样例，
服务地址
Enterprise/AcctMag/pay/BalanceChargeQuery.xml
- 请求参数
```
{
	"data": {
		"tenantId": "300",
		"pageSize": "5",
		"startTime": "2018-07-10 19:01:38",
		"state": "2",
		"endTime": "2018-09-06 19:01:38",
		"page": "1"
	}
}
``` 
- 响应参数

```
{
	"data": {
		"tenantId": "300",
		"pageSize": "5",
		"startTime": "2018-07-10 19:01:38",
		"state": "2",
		"endTime": "2018-09-06 19:01:38",
		"page": "1"
	},
	"count": 2,
	"info": [{
		"tradeAmt": "2",
		"custId": "300",
		"chargeType": "翼支付充值",
		"refund_amt": "1",
		"Id": "153382381735242206",
		"state": "2",
		"custName": "中国电信物联网公司",
		"payAmt": "1"
	},
	{
		"tradeAmt": "1",
		"custId": "300",
		"chargeType": "翼支付充值",
		"refund_amt": "1",
		"Id": "153382381735242006",
		"state": "2",
		"custName": "中国电信物联网公司",
		"payAmt": "1"
	}]
}
```