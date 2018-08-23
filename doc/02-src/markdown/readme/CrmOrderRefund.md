# 退订

- crmOrder.refund

## 请求参数:  

| 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- |
|tenantId|Long|必填|租户ID|
|type|Long|必填|退款类型，type = 1 通过prodInsId 发起退款，type =2 通过crmOrderId发起退款|
|Id|String|必填|当type=1 时，是prodInsId，当type=2 是crmOrderId|

## 响应参数:

| 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- |
|code|String|必填| 表示成功，其他值则为错误代码|
|reason|String|可选|提示信息|
|tenantId|Long|必填|租户ID|
|crmRefundId|String|必填|退订流水号|
|refundAmt|Long|必填|aep的退订金额|

- 请求示例：  

```
{
    "data":{
       "tenantId":"10007896",
       "type":1,
       "Id":"23030461528340119928"
    }
}
```

- 响应参数

```
{
    "tenantId":"10007896",
    "refundId":"230304615283401190932",
    "refundAmt":"23"
}
```
