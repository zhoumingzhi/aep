# 支付查询

- crmOrder.query

## 请求参数:  

| 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- |
|tenantId|Long|必填|租户ID|
|crmOrderId|Long|必填|计费测流水|

## 响应参数参数:  

| 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- |
|tenantId|Long|必填|租户ID|
|crmOrderId|Long|必填|计费测流水|
|tradeAmt|Long|必填|下单金额|
|payAmt|Long|必填|支付金额|

- 请求示例：  

```
{
    "data":{
       "tenantId":"10007896",
       "crmOrderId":"23030461528340119928",
    }
}
```

- 响应参数

```
{
    "tenantId":"10007896",
    "crmOrderId":"23030461528340119928",
    "tradeAmt":"12",
    "payAmt":"12"
}
```