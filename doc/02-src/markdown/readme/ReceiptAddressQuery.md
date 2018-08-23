# receipt.addr.list

## 概述
5.10.10 查询发票地址信息
对应的数据表为CM_RET_ADDR
## 更新历史

 - [20180115 zhoumingzhi] 创建本文档。

## 接口规范要求

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|custID|Long|必填|客户ID|
|2| page | int| 是|分页|
|3| pageSize | int| 是|分页大小|

## 输出结果

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|retCode|String|必填|0 表示成功，其他值则为错误代码|
|2|msg|String|可选|提示信息|
|3|custID|Long|必填|客户ID|
|4|count|Int|可选|发票地址信息|
|5|addressInfo|Array|可选|发票地址信息|

addressInfo 格式为：

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|ID|String|必填|主键ID| 
|2|name|String|必填|收款人姓名|
|3|province|String|必填|所在省份|
|4|city|String|必填|所在地市|
|5|district|String|必填|所在区|
|6|address|String|必填|街道地址|
|7|email|String|必填|邮政编码|
|8|phone|String|必填|手机号| 

## 异常
 * 返回相应的信息，并返回代码：
 
## 样例

下面是一个样例，
服务地址如下；参数参考下面格式
```
Enterprise/AcctMag/Receipt/ReceiptAddressQuery
```

```
输入参数
{
	"data": {
		"custID": "111",
	}
}
输出结果：
{
	"msg": "服务调用成功",
	"retCode": "0",
    "custID": "111",
	"addressInfo": [{
		"ID": "315174773081742651",
		"email": "424501",
		"address": "hengnan",
		"phone": "19835",
		"city": "hengyang",
		"district": "hengnan",
		"province": "hunan",
		"name": "zhou"
	},
	{
		"ID": "315174941872736419",
		"email": "424501",
		"address": "hengnan",
		"phone": "19835",
		"city": "hengyang",
		"district": "hengnan",
		"province": "hunan_update",
		"name": "zhou"
	}]
}
```