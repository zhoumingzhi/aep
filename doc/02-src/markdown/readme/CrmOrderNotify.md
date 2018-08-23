# 支付异步通知

- 注意以crm格式为准

- orderNotify

假若没有收到下面指定的响应参数，则推送没2分钟重复推送一次

- 推送参数:  

| 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- |
|tenantId|Long|必填|租户ID|
|crmOrderId|Long|必填|生成的订单流水号|
|tradeAmt|Long|必填|下单金额|
|payAmt|Long|必填|支付金额|

- 需要CRM侧响应如下参数才不继续推送:

| 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- |
|tenantId|Long|必填|租户ID|
|crmOrderId|long|必填|计费测流水号|

- 推送参数

```
{
    "data":{
       "tenantId":"10007896",
           "crmOrderId":"1223434",
           "tradeAmt":"12",
           "payAmt":"12",
    }
}
```

- 响应参数

```
{
    "tenantId":"10007896",
    "crmOrderId":"12234324434"
}
```