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

