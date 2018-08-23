# voucher.list

## 概述

5.10.1 汇款底单查询

## 更新历史

 - [20180115 zhoumingzhi] 创建本文档。

## 接口规范要求

汇款底单提交
个人平台和运营商平台统一接口
对应库表为IB_REM_RESULT

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|custID|Long|必填|客户ID|
|2|remitterName|String|必填|汇款人姓名|
|3|flag|int|必填|flag=0 运营平台查询,flag=1 个人平台查询|
|4|status|int|必填|status=0 全部查询,status=1 待审核,status=2 审核通过|
|5|startTime|Datetime|可选|生效时间|
|6|endTime|Datetime|可选|失效时间|
|7| page | int| 是 |分页数  |
|8| pageSize | int| 是 |分页大小|

## 输出结果

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|retCode|String|必填|0 表示成功，其他值则为错误代码|
|2|msg|String|可选|提示信息|
|3|custID|Long|必填|客户ID|
|4|count|int|必选|查询记录数|
|5|remitterInfo|Array|可选|汇款底单信息|

其中remitterInfo格式为：
| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|remitterName|String|必填|汇款人姓名|
|2|remitAMT|Long|必填|汇款金额|
|3|remitterBAcct|String|必填|汇款人银行账号|
|4|remitterPhone|String|必填|联系人手机|
|5|commitTime|DateTime|必填|提交时间|
|6|checkStatus|String|必填|审核状态1:待审核，2审核通过|
|7|commitType|Int|必填|汇款底单提交方式。1：扫描件 2：填写信息|
|8|picPath|String|可选|汇款底单图片路径，提交方式为1时，在界面上显示汇款底单图片|
|9|custID|String|必选|用户id|
|10|custName|String|必选|用户名|
|11|remitTime|String|必选|汇款时间|
|12|remark|String|必选|备注|
|11|ID|String|必选|底单记录ID|


## 异常
 * 返回相应的信息，并返回代码：
 
## 样例

下面是一个样例，
```
Enterprise/AcctMag/Voucher/PaymentVoucherQuery 
```

```
输入参数
{
	"data": {
		"checkStatus": "1",
		"pageSize": "4",
		"flag": "0",
		"page": "1",
		"custID": ""
		"checkStatus": "0"
	}	
}
输出结果：
{
	"remitterInfo": [{
		"remitterBAcct": "43454",
		"checkStatus": "审核通过",
		"commitTime": "2018-01-18 14:23:05.0",
		"custID": "112",
		"remitterName": "zhoumignzhi",
		"remitAMT": "345",
		"custName": "中国电信",
		"remitterPhone": "19999999 "
		"remitterPhone": "19999999 "
	},
	{
		"remitterBAcct": "2334",
		"checkStatus": "审核通过",
		"commitTime": "2017-12-28 23:18:56.0",
		"custID": "111",
		"remitterName": "zdge",
		"remitAMT": "234",
		"custName": "周明志",
		"remitterPhone": "325235"
	},
	{
		"remitterBAcct": "4xde3454",
		"checkStatus": "待审核",
		"commitTime": "2018-01-18 14:23:05.0",
		"custID": "111",
		"remitterName": "zhoumignzhi",
		"remitAMT": "345",
		"custName": "周明志",
		"remitterPhone": "19999999 "
	},
	{
		"remitterBAcct": "232",
		"checkStatus": "审核通过",
		"commitTime": "2018-01-03 11:33:04.0",
		"custID": "100",
		"remitterName": "ewew",
		"remitAMT": "23",
		"custName": null,
		"remitterPhone": "324"
	}],
	"msg": "服务调用成功",
	"retCode": "0"
}
```