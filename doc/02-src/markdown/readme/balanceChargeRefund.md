balanceCharge.reFund

## 概述

## 更新历史

 - [20170906 raoduan] 创建本文档。
 - 目前此接口只支持翼支付退款

## 接口规范要求

充值退款

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|tenantId|Long|必填|租户ID,不传就标识查询全部|
|2|Id|Long|必填|查询时候返回的充值Id|
|3|tradeAmt|Long|必填|需要退款金额|

## 输出结果
| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|retCode|String|必填|0 表示成功，其他值则为错误代码|
|2|msg|String|可选|提示信息|
|3|Id|String|必填|退订ID| 
|3|tradeAmt|long|必填|退订交易金额| 
|3|reFundAmt|long|必填|退订实际金额 当实际退款金额=0时，不要怀疑，这个时候后台正在进行异步操作| 
|4|state|long|必填|=0 标识退款成功 =1 表示没有此订单 =2 表示退款金额大于剩余可退金额 =3 是汇款底单充值，不能退款| 
|5|msg|long|必填|错误提示| 

 * 返回相应的信息，并返回代码：core.ok
 
## 样例

下面是一个样例，
服务地址
Enterprise/AcctMag/pay/BalanceChargeRefund

- 请求参数

```
{
	"data": {
		"tenantId": "300",
		"Id": "23424535351",
		"tradeAmt": "1"
	}
}
```

- 返回参数

```
{
	"data": {
		"tenantId": "300",
		"Id": "23424535351",
		"tradeAmt":"1"
	},
	"retCode":"0",
	"msg":"",
	"tenantId": "300",
	"Id": "23423424535351",
	"tradeAmt": "1",
	"reFundAmt": "1",
	"state": 1,
	"msg": "没有此订单号"
}
```