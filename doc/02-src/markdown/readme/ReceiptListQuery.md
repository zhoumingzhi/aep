# receipt.ins.list

## 概述

5.10.13 发票列表查询
对应的数据表为CM_RLIST_INFO

## 更新历史

 - [20180115 zhoumingzhi] 创建本文档。

## 接口规范要求

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|custID|Long|可选|客户ID|
|3|startTime|Datetime|可选|开始日期|
|4|endTime|Datetime|可选|截止日期|
|5|status|int|可选|发票状态1：全部2：未开票3：开票中4：已开票|
|6|flag|int|必选|flag=0 运营商门户列表查询,flag=1 个人门户列表查询|
|7| page | int| 是|分页|
|8| pageSize | int| 是|分页大小|

## 输出结果

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|code|String|必填|0 表示成功，其他值则为错误代码|
|2|msg|String|可选|提示信息|
|3|count|int|必选|返回记录个数|
|3|receiptListInfo|Array|可选|发票列表信息|

其中发票列表信息receiptListInfo为：

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|ID|Long|必填|主键ID|
|2|custID|Long|必填|客户ID|
|3|custName|String|必填|客户名称|
|4|receiptAMT|long|必填|发票金额|
|5|receiptSTime|Datetime|必填|发票申请时间|
|6|receiptTitle|String|必填|发票抬头|
|7|receiptType|Int|必填|发票性质|
|8|receiptType|Int|必填|发票性质|
|9|status|int|可选|发票状态|
|10|address|string|必选|发票地址信息|
|11|remitName|string|必选|发票收件人|

## 异常
 * 返回相应的信息，并返回代码：
 
## 样例

下面是一个样例，
服务地址如下
```
Enterprise/AcctMag/Receipt/ReceiptListQuery
```

```
输入参数
{
	"data": {
		"flag": "0",
		"custID": "111",
		"pageSize": "5",
		"startTime": "2018-01-01 17:08:47",
		"endTime": "2018-01-10 17:08:47",
		"page": "1",
		"status": "1"
	}	
}
输出结果：
{
	"msg": "服务调用成功",
	"retCode": "0",
	"count":2,
	"receiptListInfo": [{
		"address": "gdgzthaddress",
		"receiptType": "1",
		"receiptSTime": "2018-01-03 17:08:47.0",
		"receiptTitle": "zhou",
		"custID": "111",
		"ID": "1112324",
		"receiptAMT": "12",
		"custName": "zhou",
		"status": "未开票"
	}]
}
```