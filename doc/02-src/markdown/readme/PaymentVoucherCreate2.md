# voucher.create

## 概述

5.10.1 汇款底单提交

## 更新历史

 - [20180115 zhoumingzhi] 创建本文档。

## 接口规范要求

汇款底单提交
对应的数据库表为IB_REM_RESULT

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|custID|Long|必填|客户ID|
|2|commitType|Int|必填|汇款底单提交方式。1：扫描件 2：填写信息|
|3|picPath|String|汇款方式为1时必填|汇款底单扫描图片路径|
|4|remitterPhone|String|必填|联系人手机|
|5|remitterName|String|汇款方式为2时必填|汇款人姓名|
|6|remitAMT|Long|汇款方式为2时必填|汇款金额|
|7|remitterBAcct|String|汇款方式为2时必填|汇款人银行账号|
|8|commitTime|DateTime|汇款方式为2时必填|提交时间|

## 输出结果

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|retCode|String|必填|0 表示成功，其他值则为错误代码|
|2|msg|String|可选|提示信息|
|3|custID|Long|必填|客户ID|
|4|ID|Long|必填|主键ID|
|5|remitterName|String|必填|汇款人姓名|
|6|remitAMT|Long|必填|汇款金额|
|7|remitterBAcct|String|必填|汇款人银行账号|
|8|remitterPhone|String|必填|联系人手机|
|9|commitTime|DateTime|必填|提交时间|
|10|checkStatus|int|必填|审核状态，1：待审核2：审核通过|

## 异常
 * 返回相应的信息，并返回代码：
 
## 样例

下面是一个样例，
```
Enterprise/AcctMag/Voucher/PaymentVoucherCreate
```

```
输入参数
{
	"data": {
		"remitAMT": "345",
		"commitType": "2",
		"custID": "111",
		"picPath": " ",
		"commitTime": "2018-01-18 14:23:05",
		"remitterBCardID": "43454",
		"remitterPhone": "19999999 ",
		"remitterName": "zhoumignzhi",
		"remark": "hahh"
		}
}
输出结果：
{
	"msg": "服务调用成功",
	"checkStatus": "审核未通过",
	"retCode": "0",
	"commitTime": "2018-01-18 14:23:05",
	"remitterBCardID": "43454",
	"custID": "112",
	"remitterName": "zhoumignzhi",
	"remitAMT": "345",
	"remitterPhone": "19999999",
	"ID": "993434"
}
```