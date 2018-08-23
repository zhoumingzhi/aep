# 退订异步通知

- 注意：以crm边格式为准
- refundNotify

假若没有收到下面指定的响应参数，则推送没2分钟重复推送一次

## 推送参数:  

| 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- |
|tenantId|Long|必填|租户ID|
|refundId|String|必填|退订流水号|
|refundAmt|long|必填|退订金额|

## 需要crm测响应如下参数，否则一直推送

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