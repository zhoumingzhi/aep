# order.list

## 概述

5.9.4  订单查询

## 更新历史

 - [20180201  zhoumingzhi] 创建本文档。

## 接口规范要求

创建订单

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|custID|Long|必填|客户ID|
|2|orderType|Int|必填|订单类型 0: 新购,1:退款,2:续费,3:全部|
|3|acctType|Int|必填|账户类型acctType 0:全部账户，1: 个人账户 2: 企业账户|
|4|payStatus|String|必须|支付状态 payStatus=0：未支付 2： 已支付 3：全部|
|8|startTime|Datetime|可选|生效时间|
|9|endTime|Datetime|可选|失效时间|
|10|flag|int|必选|flag=0,运营商查询列表,flag=1,查询|
|11| page | int| 是|分页|
|12| pageSize | int| 是|分页大小|

## 输出结果
| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|retCode|String|必填|0 表示成功，其他值则为错误代码|
|2|msg|String|可选|提示信息|
|3|ID|String|必选|订单ID|
|4|orderID|String|必填|订单编号|
|5|custID|String|必填|客户ID|
|6|custName|String|必填|客户名字|
|7|prodID|String|必填|产品ID|
|8|prodType|String|必填|产品类型|
|9|prodName|String|必填|产品名称|
|10|orderTime|Datetime|必填|创建时间|
|11|payTime|Datetime|必填|支付时间|
|12|effTime|Datetime|必填|订单开始计费时间|
|13|payStatus|String|必填|支付状态|
|14|amt|String|必填|应付金额|



## 异常
 * 返回相应的信息，并返回代码：core.ok
 
## 样例

下面是一个样例，
服务地址如下
```
Enterprise/SubscriptionMag/OrderQuery
```

输入参数：
```
{
	"data": {
		"flag": "0",
		"pageSize": "10",
		"startTime": "2018-01-01 16:08:59",
		"endTime": "2019-01-20 01:08:59",
		"page": "1",
		"payStatus": "1"
	}    
}
```

输出结果：
```
{
	"msg": "服务调用成功",
	"orderInfoList": [{
		"orderType": "续费",
		"orderID": "1",
		"payTime": "2018-01-02 15:02:37.0",
		"custID": "111",
		"prodName": "流量",
		"amt": "120",
		"effTime": "2018-01-10 15:08:59.0",
		"ID": "0",
		"prodID": "412",
		"custName": "周明志",
		"payStatus": "已支付"
	},
	{
		"orderType": "续费",
		"orderID": "2",
		"payTime": "2018-01-03 15:10:02.0",
		"custID": "111",
		"prodName": "语音",
		"amt": "23",
		"effTime": "2018-01-10 15:08:59.0",
		"ID": "1",
		"prodID": "411",
		"custName": "周明志",
		"payStatus": "已支付"
	},
	{
		"orderType": "续费",
		"orderID": "2",
		"payTime": "2018-01-02 16:02:52.0",
		"custID": "110",
		"prodName": "语音",
		"amt": "123",
		"effTime": "2018-02-07 16:03:35.0",
		"ID": "2",
		"prodID": "412",
		"custName": "邢晓云",
		"payStatus": "未支付"
	}],
	"retCode": "0"
}
```



