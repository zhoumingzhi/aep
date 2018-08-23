# receipt.ins.create

## 概述

根据发票信息 表cm_ret_info、发票地址表cm_ret_addr、发票金额receiptAmt生成cm_rlist_info实例

## 更新历史

 - [20180115 zhoumingzhi] 创建本文档。

## 接口规范要求

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|custID|Long|必选|客户ID|
|2|receiptInfoID|Long|必选|发票信息ID|
|3|receiptAddrID|Long|必选|发票地址ID|
|4|receiptAmt|Long|必选|发票金额|
|5|retID|String|必选|订单主键ID，用逗号,分开|
|6|status|int|必选|发票索取列表状态，0：未开票，1：已开票|

## 输出结果

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|code|String|必填|0 表示成功，其他值则为错误代码|
|2|msg|String|可选|提示信息|
|3|receiptID|Long|必选|生成的获取发票的信息ID|


## 异常
 * 返回相应的信息，并返回代码：
 
## 样例

下面是一个样例，
服务地址如下
```
Enterprise/AcctMag/Receipt/ReceiptInsCreate
```

```
输入参数
{
	"data": {
		"custID": "111",
		"receiptInfoID": "1213",
		"receiptAddrID": "123",
		"receiptAmt": "343",
		"retID": "344,435",
		"status":"1" 
	}	
}
输出结果：
{
	"msg": "服务调用成功",
	"retCode": "0",
	"ID": "1112324"
}
```