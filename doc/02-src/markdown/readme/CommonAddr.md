# get.addr 

## 概述


## 更新历史

## 接口规范要求
获取三级地址
输入上一级地址编码，获取下一级地址编码和名称。当想获取省级信息，输入中国编码8100000

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|regionID|Long|必填|地址编码|

## 输出结果

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|retCode|String|必填|0 表示成功，其他值则为错误代码|
|2|msg|String|可选|提示信息|
|3|regionInfo|Array|必选|地址列表|

其中地址格式RegionInfo为

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|regionName|String|必填|地址名称|
|2|regionID|String|必填|地址ID|



## 异常
 * 返回相应的信息，并返回代码：
 
## 样例

下面是一个样例，
服务地址如下:
```
Enterprise/AcctMag/Receipt/CommonAddr
```

```
输入参数：
{
	"data": {
		"regionID": "8140000"
	}    
}

输出结果：
{
	"msg": "服务调用成功",
	"retCode": "0",
	"regionInfo": [{
		"regionID": "8140100",
		"regionName": "太原市"
	},
	{
		"regionID": "8140200",
		"regionName": "大同市"
	},
	{
		"regionID": "8140300",
		"regionName": "阳泉市"
	},
	{
		"regionID": "8140400",
		"regionName": "长治市"
	},
	{
		"regionID": "8140500",
		"regionName": "晋城市"
	},
	{
		"regionID": "8140600",
		"regionName": "朔州市"
	},
	{
		"regionID": "8140700",
		"regionName": "晋中市"
	},
	{
		"regionID": "8140800",
		"regionName": "运城市"
	},
	{
		"regionID": "8140900",
		"regionName": "忻州市"
	},
	{
		"regionID": "8141000",
		"regionName": "临汾市"
	},
	{
		"regionID": "8141100",
		"regionName": "吕梁市"
	}]
}
```



