# receipt.get.query

## 概述
5.10.12 发票索取状态更新
对应的数据表为IB_RET_REQ
## 更新历史

 - [20180115 zhoumingzhi] 创建本文档。

## 接口规范要求

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|custID|Long|必填|客户ID|
|2|ID|Long|必填|发票索取主键ID|
|2|status|Long|必填|发票更新状态 0：未索取，1:已经索取|


## 输出结果

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|retCode|String|必填|0 表示成功，其他值则为错误代码|
|2|msg|String|可选|提示信息|
|3|custID|Long|必填|客户ID|

## 异常
 * 返回相应的信息，并返回代码：
 
## 样例

下面是一个样例，
服务地址如下；参数参考下面格式
```
Enterprise/AcctMag/Receipt/ReceiptGetListUpdate
```

```
输入参数
{
	"data": {
		"custID": "10008138",
		"ID": "345,346",
		"status": "3"
	}
}
输出结果：
{
	"msg": "服务调用成功",
	"custID": "10008138",
	"retCode": "0"
}
```