# acct.cust.info

## 概述

5.8.4 客户账户查询

## 更新历史
 - [20180731 chenjiadong] 添加实时费用

## 接口规范要求
个人门户和运营商门户统一接口

## 输入参数


| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
| 1 | custID | Long| 是| 账户信息|
| 1 | acctType | Long| 是| 账户类型 =0 全部 =1 个人 =2 企业|
| 3 | flag | int| 是| falg=0表示运营商门户 查询列表 flag=1 表示个人门户查询 查询详情|
| 4| page | int| 是|分页|
| 5| pageSize | int| 是|分页大小|


## 输出结果

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|retcode|String|必填|0表示成功，其他值表示错误代码|
|2|msg|String|可选|提示信息|
|3|count|int|可选|列表个数|
|4|cAccountInfo|Array|可选|客户账户信息|

其中cAccountInfo客户账户信息格式

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|custID|Long|必填|客户ID|
|2|custName|String|必填|客户名称|
|3|acctStatus|String|必填|账户状态 AS10:正常,AS20:欠费,AS30:销户|
|4|acctType|String|必填|账户类型 enterprise：企业账户，personal：个人账户|
|5|amt|long|必填|余额|
|6|unwoffAMT|long|必填|未结清余额|
|7|userStatus|String|必填|用户状态 1:未激活，2：已激活|
|8|realamt|long|必填|实时费用|
|9|refillHisInfo|Array|可选|充值历史信当flag=0 不输出|
|10|billInfo|Array|可选|账单信息 当flag=0 不输出|
|11|orderInfo|Array|可选|订单信息 当flag=0 不输出|

充值历史refillHisInfo格式

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|refillTime|datetime|必填|充值时间|
|2|refillAMT|long|必填|充值金额|
|3|refillMethod|String|必填|充值方式，固定填写“线下汇款”|

账单信息billInfo格式

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|Id|String|必填|记录主键Id|
|2|payStatus|String|必填|支付状态|
|3|billCycle|String|必填|账期|
|4|acctItemName|Long|必填|费用名称|
|5|amt|Long|必填|应付金额（含税）|
|6|unwoffAMT|Long|必填|欠费金额|
|7|payType|String|必填|付款方式|

订单信息orderInfo格式

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|prodID|String|必填|产品编码|
|2|prodName|String|必填|产品名称|
|3|payTime|Datetime|必填|支付时间|
|4|payStatus|String|必填|支付状态|
|5|amt|Long|必填|应付金额|
|6|prodType|Long|必填|产品类型|
|5|amt|Long|必填|应付金额|
|6|orderID|Long|必填|订单id|
|7|effTime|String|必填|订单生效时间|

## 异常
 * 返回相应的信息，并返回代码：core.ok
 
## 样例

下面是一个样例，
```
Enterprise/CustomerMag/CAccountInfoQuery
```
- 对于运营商门flag=0
```
输入参数
{
	"data": {
		"pageSize": "5",
        "page":"1",
		"flag": "0",
		"custID": "111"
	}    
    
}

输出结果
{
	"cAccountInfo": [{
		"acctStatus": "正常",
		"unwoffAMT": "500",
		"userStatus": "正常",
		"custID": "111",
		"acctType": "个人账户",
		"amt": "234",
		"realamt":123,
		"custName": "周明志"
	},
	{
		"acctStatus": "欠费",
		"unwoffAMT": "23",
		"userStatus": "正常",
		"custID": "110",
		"acctType": "企业账户",
		"amt": "233",
		"realamt":123,
		"custName": "邢晓云"
	},
	{
		"acctStatus": "销账",
		"unwoffAMT": "242",
		"userStatus": "正常",
		"custID": "112",
		"acctType": "个人账户",
		"amt": "23243",
		"realamt":123,
		"custName": "中国电信"
	}],
	"count":"5",
	"msg": "服务调用成功",
	"retCode": "0"
}
```
- 对于个人门户查询 flag=1
```
输入参数
{
	"data": {
		"pageSizes": "5",
		"flag": "1",
		"pageno": "1",
		"custID": "111"
	}    
}

输出参数
{
	"cAccountInfo": {
		"acctStatus": "正常",
		"userStatus": "正常",
		"unwoffAMT": "500",
		"billInfo": [{
			"unwoffAMT": "0",
			"payType": "线下汇款",
			"payStatus": "已支付",
			"acctItemName": "zhoumingzhi",
			"amt": "434",
			"billCycle": "12"
			"orderType":"1",
			"orderID":"2345351",
			"efftime":"2018-01-18 14:23:05.0"
		},
		{
			"unwoffAMT": "0",
			"payType": "线下汇款",
			"payStatus": "已支付",
			"acctItemName": "dming",
			"amt": "23",
			"billCycle": "11"
			"orderType":"1",
			"orderID":"2345351",
			"efftime":"2018-01-18 14:23:05.0"
		},
		{
			"unwoffAMT": "232",
			"payType": "线下汇款",
			"payStatus": "未支付",
			"acctItemName": "zhoumingzhi",
			"amt": "232",
			"billCycle": "12"
			"orderType":"1",
			"orderID":"2345351",
			"efftime":"2018-01-18 14:23:05.0"
		},
		{
			"unwoffAMT": "32",
			"payType": "线下汇款",
			"payStatus": "未支付",
			"acctItemName": null,
			"amt": "34",
			"billCycle": "11"
			"orderType":"1",
			"orderID":"2345351",
			"efftime":"2018-01-18 14:23:05.0"
		},
		{
			"unwoffAMT": "211",
			"payType": "线下汇款",
			"payStatus": "未支付",
			"acctItemName": "zhou",
			"amt": "234",
			"billCycle": "11"
			"orderType":"1",
			"orderID":"2345351",
			"efftime":"2018-01-18 14:23:05.0"
		}],
		"custID": "111",
		"amt": "234",
		"refillHisInfo": [{
			"refillMethod": "线下汇款",
			"refillTime": "2018-01-18 14:23:05.0",
			"refillAMT": "345"
		},
		{
			"refillMethod": "线下汇款",
			"refillTime": "2017-12-28 23:18:56.0",
			"refillAMT": "234"
		}],
		"OrderInfo": [{
			"payTime": "2018-01-02 15:02:37.0",
			"prodName": "流量",
			"amt": "120",
			"updateTime": "2018-02-21 15:09:06.0",
			"prodID": "412",
			"prodType": "2",
			"payStatus": "已支付"
		},
		{
			"payTime": "2018-01-03 15:10:02.0",
			"prodName": "语音",
			"amt": "23",
			"updateTime": "2018-01-23 15:10:21.0",
			"prodID": "411",
			"prodType": "1",
			"payStatus": "未支付"
		}],
		"custName": "周明志"
	},
	"msg": "服务调用成功",
	"retCode": "0"
}
```


