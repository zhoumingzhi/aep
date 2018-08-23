# crm下单

- crmOrder.create

 ## 请求参数:  

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

# 支付查询

- crmOrder.query

- 请求参数:  

| 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- |
|tenantId|Long|必填|租户ID|
|crmOrderId|Long|必填|计费测流水|

- 响应参数参数:  

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

# 支付竣工 

- crmOrder.finish

 ## 请求参数:  

 | 参数 | 类型 | 是否必须 |说明 |
 | ---- | ---- | ---- | ---- |
|tenantId|Long|必填|租户ID|
|crmOrderId|Long|必填|计费测流水|
|prodInsInfo|ArrayList|必填|订购实例列表|

- 其中prodInsInfo格式为

 | 参数 | 类型 | 是否必须 |说明 |
 | ---- | ---- | ---- | ---- |
|prodInsId|Long|必填|商品实例|
|prodType|Long|必填|商品类型|
|sellerId|Long|必填|商家|
|tradeAmt|Long|必填|金额|
|prodName|String|必填|产品名称|
|effTime|yyyy-MM-dd HH:mm:ss |必填| 暂时默认下单时间就是竣工时间|
|expTime|yyyy-MM-dd HH:mm:ss |必填| 失效时间|
|subProdInfo|ArrayList|选填|商品从属信息表|

- 其中subProdInfo格式为

 | 参数 | 类型 | 是否必须 |说明 |
 | ---- | ---- | ---- | ---- |
|prodInsId|Long|必填|商品实例|
|prodType|Long|必填|商品类型|
|sellerId|Long|必填|商家|
|prodName|String|必填|产品名称|
|tradeAmt|Long|必填|金额|

## 响应参数:

| 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- |
|tenantId|Long|必填|租户ID|
|code|String|必填| 表示成功，其他值则为错误代码|
|reason|String|可选|提示信息|

- 请求参数
```
{
	"data":{
	"tenantId":"10007896",
	"crmOrderId":"10007896"
	"prodInsInfo": [
            {
                "prodInsId": "12324", 
                "prodType": "12", 
                "sellerId": "213", 
                "tradeAmt": 23, 
                "prodName": "订单1主机1", 
                "effTime": "2018-08-06 11:28:40", 
                "expTime": "2018-08-07 11:28:40", 
                "subProdInfo": [
                    {
                        "prodInsId": "1232445", 
                        "prodType": "23", 
                        "prodName": "网络", 
                        "tradeAmt": 3234
                    }, 
                    {
                        "prodInsId": "12332445", 
                        "prodType": "233", 
                        "prodName": "硬盘", 
                        "tradeAmt": 324
                    }
                ]
            }, 
            {
                "prodInsId": "1232423", 
                "prodType": "1232", 
                "sellerId": "2324313", 
                "tradeAmt": 23, 
                "prodName": "订单1主机2", 
                "effTime": "2018-08-06 11:28:40", 
                "expTime": "2018-08-07 11:28:40"
            }
        ]
	}
}
```

- 响应参数

```
{
	"tenantId":"10007896",
	"code":"core.ok",
	"reason":""
}
```

# 退订前查询

- crmRefundInfo.query

- 请求参数:  

| 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- |
|tenantId|Long|必填|租户ID|
|type|Long|必填|退款类型，type = 1 通过prodInsId 发起退款，type =2 通过crmOrderId发起退款|
|Id|String|必填|当type=1 时，是prodInsId，当type=2 是crmOrderId|

- 响应参数:

| 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- |
|code|String|必填| 表示成功，其他值则为错误代码|
|reason|String|可选|提示信息|
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
    "refundAmt":"123",
}
```

# 退订

- crmOrder.refund

- 请求参数:  

| 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- |
|tenantId|Long|必填|租户ID|
|type|Long|必填|退款类型，type = 1 通过prodInsId 发起退款，type =2 通过crmOrderId发起退款|
|Id|String|必填|当type=1 时，是prodInsId，当type=2 是crmOrderId|

响应参数:

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


# 退订异步通知
- 注意：以crm边格式为准
- refundNotify

假若没有收到下面指定的响应参数，则推送没2分钟重复推送一次

- 推送参数:  

| 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- |
|tenantId|Long|必填|租户ID|
|refundId|String|必填|退订流水号|
|refundAmt|long|必填|退订金额|

- 需要crm测响应如下参数，否则一直推送

 | 参数 | 类型 | 是否必须 |说明 |
 | ---- | ---- | ---- | ---- |
|tenantId|Long|必填|租户ID|
|refundId|String|必填|退订流水号|


- 推送参数

```
{
    "data":{
       "tenantId":"10007896",
       "refundId":"1223433454"
    }
}
```

- 响应参数

```
{
    "tenantId":"10007896",
    "refundId":"1223433454",
    "refundAmt":12
}
```
