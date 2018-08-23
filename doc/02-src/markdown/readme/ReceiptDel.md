# receipt.del

## 概述

5.10.5 删除发票信息
对应的数据表为CM_RET_INFO

## 更新历史

 - [20180115 zhoumingzhi] 创建本文档。

## 接口规范要求

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|ID|Long|必填|主键ID|
|2|custID|Long|必填|客户ID|

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
Enterprise/AcctMag/Receipt/ReceiptDel

```


## 异常
 * 返回相应的信息，并返回代码：
 
## 样例

下面是一个样例，
服务地址如下
```
Enterprise/AcctMag/Receipt/ReceiptDel

```

```
输入参数
{
	"data": {
		"ID": "315176333946944656"
		"custID": "111"
	}
}

输出结果：
{
	"msg": "服务调用成功",
	"custID": "111",
	"ID": "315176333946944656",
	"retCode": "0"
}
```