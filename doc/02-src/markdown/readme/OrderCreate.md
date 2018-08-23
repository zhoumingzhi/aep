# OrderCreate

## 概述

5.9.1  创建订单

## 更新历史

 - [20170906 raoduan] 创建本文档。
## 接口规范要求
创建订单

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|CustID|Long|必填|客户ID|
|2|OrderType|Int|必填|订单类型|
|3|ProductID|String|必填|产品编码|
|4|ProductName|String|必填|产品名称|
|5|PayTime|Datetime|必填|支付时间|
|6|PayStatus|String|必填|支付状态|
|7|AMT|Long|必填|应付金额|
|8|effTime|Datetime|必填|生效时间|
|9|expTime|Datetime|可选|失效时间|

## 输出结果
| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|RetCode|String|必填|0 表示成功，其他值则为错误代码|
|2|Msg|String|可选|提示信息|
|3|OrderID|String|必填|订单编号|
|4|CreateTime|DateTime|必填|创建时间|
|5|CustID|Long|必填|客户ID|



## 异常
 * 返回相应的信息，并返回代码：core.ok
 
## 样例

下面是一个样例，
服务地址如下；参数参考下面CCR格式
```
Enterprise/SubscriptionMag/{version}/ OrderCreate
http://10.142.90.42:9100/native/balance.query
```

输入参数：
```
输入用户号码1064910009928，按帐户查询
	"CCR": {
	    "AcctID": "500000001"
	}
```

输出结果：
```
"CCA": {
        "RetCode": "0", 
        "Msg": "服务调用成功",
        "Balance-Information": {
           "AcctID" : test,
           "Balance" : test,
           "UnwoffAMT" : test,
           "ReceiptAMT" : test
    }
}
```



