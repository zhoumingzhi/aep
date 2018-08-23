# crm下单

- crmOrder.create

 ## 请求参数  

| 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- |
|tenantId|Long|必填|租户ID|
|orderSn|Long|必填|crm订单编号|
|tradeAmt|Long|必填|crm订单金额|
|googsInfo|String|必填|订单详情|

## 响应参数:

| 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- |
|tenantId|Long|必填|租户ID|
|code|String|必填| 表示成功，其他值则为错误代码|
|reason|String|可选|提示信息|
|path|String|必选|下单支付path|
|orderSn|Long|必填|crm订单编号|
|crmOrderId|Long|必填|生成的订单流水号|

- 请求参数
```
{
    "data": {
        "tenantId": "300", 
        "orderSn": "12342", 
        "googsInfo": "这是一个下单订单",
        "tradeAmt":123
    }
}
```

- 响应参数

```
{
    "tenantId":10007897,
	"path":"http://132.246.27.77:20010/portalweb/pay.html#/order/10007897/153299972004484332",
    "orderSn":"99010461528333119953",
    "crmOrderId":"23010461528340119928"
}
```