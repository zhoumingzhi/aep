# bestpay.order

## 概述

aep前端在下单进行进行翼支付支付时，预先获取的必要参数

## 更新历史

 - [20180522  zhoumingzhi] 创建本文档。

 ## 输入参数
 
  | 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
  |1|custId|varchar|必填|下单的客户|
  |2|amt|varchar|必填|下单金额|
  |3|goodsInfo|varchar|必填|商品描述|
 

## 输出参数
 
  | 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
  |1|outTradeNo|varchar|必填|商户侧订单的唯一标志.生成规则:租户ID_内部流水|
  |2|merchantNo|varchar|必填|商户号|
  |3|tradeAmt|int|必填|订单金额|
  |4|ccy|varchar|必填|币种，默认传156|
  |5|requestTime|datetime|必填|订单请求时间，格式"yyyy-MM-dd   HH:mm:ss"|
  |6|tradeChannel|varchar|必填|交易渠道，在翼支付商服平台签约时会提供|
  |7|accessCode|varchar|必填|接入方标识码，在翼支付商服平台签约时会提供|
  |8|mediumType|varchar|必填|介质类型，在翼支付商服平台签约时会提供|
  |9|mediumNo|varchar|必填|介质号，在翼支付商服平台签约时会提供|
  |10|goodsInfo|varchar|必填|商品名称|
  |11|subject|varchar|必填|订单标题|
  |12|operator|varchar|必填|操作员编号|
  |13|notifyUrl|varchar|必填|支付回调商户地址 |
  |14|storeCode|varchar|必填|门店号|
  |15|storeName|varchar|必填|门店名称|
  |16|rate|int|必填|汇率|
  |17|foreignCcy|varchar|必填|外币币种|
  |18|foreignAmount|int|必填|外币金额|
  |19|ledgerAccount|varchar|必填|分账信息|
  |20|operState|varchar|必填|1下单\n            2支付回调成功\n            3发起退款\n            4退款回调成功|
  |21|updateTime|datetime|必填|更新时间|
  |22|remark|varchar|必填|备注|
  |23|custId|bigint|必填|自增序列，取自全局序列|





