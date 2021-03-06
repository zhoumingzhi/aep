# receipt.list.update

## 概述

发票列表状态更新
对应的数据表为CM_RLIST_INFO

## 更新历史

 - [20180115 zhoumingzhi] 创建本文档

## 接口规范要求

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|ID|Long|必选|主键ID|
|2|custID|Long|必选|客户ID|
|3|status|int|可选|发票状态1：全部2：未开票3：开票中4：已开票|

## 输出结果

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|code|String|必填|0 表示成功，其他值则为错误代码|
|2|msg|String|可选|提示信息|
|3|ID|int|必选|返回主键ID|
|4|custID|int|必选|客户ID|


## 异常
 * 返回相应的信息，并返回代码：
 
## 样例

下面是一个样例，
服务地址如下
```
Enterprise/AcctMag/Receipt/ReceiptListUpdate
```

```
输入参数
{
	"data": {
        "ID":"315197997620116596"
        "custID":"111"
        "status":"3"
	}	
}
输出结果
{
	"custID":"111",
	"ID":"315197997620116596",
	"msg": "服务调用成功",
	"retCode": "0",
}
```