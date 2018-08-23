# voucher.check

## 概述

  汇款底单图片提交确认

## 更新历史

 - [20180115 zhoumingzhi] 创建本文档

## 接口规范要求

对应的数据库表为IB_REM_RESULT

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|ID|Long|必填|汇款底单主键ID|
|2|custID|Long|必填|客户ID|
|3|remitterName|String|必填|汇款人姓名|
|4|remitAMT|Long|必填|汇款金额|
|5|remitterBAcct|String|可填|汇款人银行账号|
|6|remark|String|可选|备注|
|7|operCode|String|必选|操作人员编号|

## 输出结果

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|retCode|String|必填|0 表示成功，其他值则为错误代码|
|2|msg|String|可选|提示信息|
|3|custID|Long|必填|客户ID|
|4|ID|Long|必填|主键ID|

## 异常
 * 返回相应的信息，并返回代码：
 
## 样例

下面是一个样例，
服务地址如下
```
Enterprise/AcctMag/Voucher/PaymentVoucherPicCheck
```

```
输入参数
{
	"data": {
		"ID":"12134355",
		"remitAMT": "345",
		"custID": "111",
		"remitterName": "zhoumignzhi",
		"remark": "hahh"
		}
}
输出结果
{
	"msg": "服务调用成功",
	"retCode": "0",
	"ID": "12134355",
	"custID": "111"
}
```