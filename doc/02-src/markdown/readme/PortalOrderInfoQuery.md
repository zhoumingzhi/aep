portalOrder.query
## 概述

## 更新历史

 - [20170906 raoduan] 创建本文档。

## 接口规范要求

支付网关获取订单参数

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|tenantId|Long|必填|租户ID|
|3|crmOrderId|String|必填|crm下单ID| 

## 输出结果
| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|retCode|String|必填|0 表示成功，其他值则为错误代码|
|2|msg|String|可选|提示信息|
|3|tradeAmt|long|必选|下单金额|
|4|amt|long|必选|账户余额|
|5|state|int|必填|状态码 =0 表示没有此订单号 =1 表示正等待下单 =2 已经支付 =3 超时订单关闭 |
|6|deadTime|String|可选|截止时间 当state=0此参数才生效 |
|7|googsInfo|String|必填|订单详情|
|8|subject|String|必填|订单主题|
|9|channel|String|必填|租户类型 =aep 预付费 =crm 外部收费，后付费|
|10|msg|String|必填|状态对应的消息|


## 异常
 * 返回相应的信息，并返回代码：core.ok
 
## 样例

下面是一个样例，
服务地址
```
Enterprise/AcctMag/pay/PortalOrderInfoQuery.xml
{
	"tradeAmt": 12,
	"data": {
		"tenantId": "300",
		"crmOrderId": "153266228081548982"
	},
	"subject": "租户300订单153266228081548982共12分",
	"deadTime": "2018-08-07 11:01:38",
	"amt": 44,
	"state": 0,
	"goodsInfo": ""
}
```