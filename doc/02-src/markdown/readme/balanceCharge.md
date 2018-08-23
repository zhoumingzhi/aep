balanceCharge
## 概述

## 更新历史

 - [20170906 raoduan] 创建本文档。

## 接口规范要求

余额充值

## 输入参数


| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|tenantId|Long|必填|租户ID|
|2|tradeAmt|Long|必填|充值金额| 
|3|payType|long|必填|=1 翼支付，=2 微信支付，3= 支付宝支付|
|4|bankCode|String|必填|前端传过来的银行编码|
|5|frontNotifyUrl|String|必填|前端传过来的回调地址|
|6|goodsInfo|String|必填|前端传过来的商品描述|
|7|subject|String|必填|前端传过来的商品主题|

## 输出结果
| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|success|Boolean|必填|true or fail|
|2|info|ArrayList|必填|下单返回的参数，当success=fail,此参数为空|

其中`info`为

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|institutionCode|String|必填|商户注册时申请的ca证书编号，与商户号相同|
|2|institutionType|String|必填|固定传“MERCHANT”|
|3|service|String|必填|固定传“mobile.securitypay.pay”|
|4|merchantNo|String|必填|商服中心注册后获得的商户号|
|5|subMerchantNo|String|必填|固定传空|
|6|outTradeNo|String|必填|下单接口中的outTradeNo参数|
|7|tradeprodNo|String|必填|下单接口中的tradeprodNo参数|
|8|tradeNo|String|必填|下单接口返回的tradeNo参数|
|9|tradeAmt|String|必填|交易金额，单位(分)，如12.55元传1255|
|10|ccy|String|必填|固定传156|
|11|subject|String|必填|订单标题|
|12|goodsInfo|String|选填|商品信息摘要|
|13|mediumType|String|必填|固定传WIRELESS|
|14|tradeChannel|String|必填|固定传WEB|
|15|requestDate|String|必填|请求时间|
|16|frontNotifyUrl|String|选填|用于在用户完成交易后返回的前台url地址，如不传则前台将不通知商户支付结果|
|17|bankCode|String|选填|直跳网银银行编码|
|18|signType|String|必填|固定填CA|
|19|sign|String|必填|签名|

## 异常
 * 返回相应的信息，并返回代码：core.ok
 
## 样例

下面是一个样例，
```
服务地址
Enterprise/AcctMag/pay/BalanceChargeByBestpay.xml
{
	"retCode":"",
	"msg":"",
	"result": true,
	"id": "0|153146710289138151|10017443|153146710300265132",
	"info": {
		"tradeAmt": "1",
		"tradeNo": "20180713100000210002106120703538",
		"subject": "23",
		"sign": "iX+6wE3M+dQEJHR2vaLpSQYMLN5EQr9E28nWu6lAWk\/YfDhKrEWG4QRVll4a03E9DYYFcO3k8w46D3HJXAUG9cPxtGa++h80Ic56tfkxvnQNYjpsUUaTeKkXCS0tm2OgsuSgLG3ojV9yAPackbgVfGoOH3K6Ml7CQ\/4nBzIJi28=",
		"subMerchantNo": "",
		"institutionType": "MERCHANT",
		"institutionCode": "3178031195590341",
		"service": "mobile.securitypay.pay",
		"outTradeNo": "0|153146710289138151|10017443|153146710300265132",
		"ccy": "156",
		"mediumType": "WIRELESS",
		"requestDate": "2018-07-13 15:31:44",
		"signType": "CA",
		"tradeprodNo": "2018071317TPPIOP1110000122162709",
		"goodsInfo": "ee",
		"merchantNo": "3178031195590341",
		"tradeChannel": "WEB"
	}
}
```