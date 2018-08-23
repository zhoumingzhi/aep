# DiscountTariffUpdate

## 概述

更新产品优惠资费信息接口(重叠时间段内，不允许存在多个优惠资费)


## 更新历史

 - [20180122 xingxy] 创建本文档。
## 接口规范要求
更新产品优惠资费信息。

## 输入参数

| 编号 | 参数 | 类型 | 名称 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 1 | discountTariffID | UTF8String| 优惠资费ID | 是 | |
| 2 | tariffName | UTF8String| 资费名称 | 是 | |
| 3 | tariffType | Integer64| 资费类型 | 是 | 5：优惠资费|
| 4 | discountType | Enumerated| 优惠类型 | 是 | 1：打折 2: 减免|
| 5 | discountValue | Integer64| 优惠参考值 | 是 | |
| 6 | discountMtrValue | Integer64| 优惠计量值 | 是 | |
| 7 | discountMtrUnit | Integer64| 优惠计量单位 | 是 | |
| 8 | discountRefCounterType | Enumerated| 优惠参考类型 | 是 |1：费用 2：使用量 |
| 9 | discountRefItemtype | Integer64| 优惠可参考计量类型，也可参考账目类型 | 是 | |
| 10 | effTime | Time| 生效时间 | 是 | |
| 11 | expTime | Time| 失效时间 | 否 | |
| 12 | itemID | UTF8String| 产品ID | 是 | |


## 输出结果
| 参数 | 层级 | 类型 | 名称 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| retCode | 1 | Unsigned32 | 业务级结果代码 | 是 | |
| msg | 1 | UTF8String | 错误描述 | 是 | |
| discountTariffInfo | 1 | Grouped | 优惠资费明细 | 是 | |
| discountTariffID | 2 | UTF8String | 优惠资费ID | 是 | |
| tariffName | 2 | UTF8String | 资费名称 | 是 | |
| tariffType | 2 | Integer64 | 资费类型 | 是 | |
| discountType | 2 | Enumerated | 优惠类型 | 是 | |
| discountValue | 2 | Integer64 | 优惠参考值 | 是 | |
| discountMtrValue | 2 | Integer64 | 优惠计量值 | 是 | |
| discountMtrUnit | 2 | Integer64 | 优惠计量单位 | 是 | |
| discountRefCounterType | 2 | Enumerated | 优惠参考类型 | 是 | |
| discountRefItemtype | 2 | Integer64 | 优惠可参考计量类型，也可参考账目类型 | 是 | |
| effTime | 2 | Time | 生效时间 | 是 | |
| expTime | 2 | Time | 失效时间 | 是 | |
| updateTime | 2 | Time | 创建时间 | 是 | |
| itemID | 2 | UTF8String | 产品id | 是 | |
## 异常
 * 返回相应的信息，并返回代码：core.ok
 
## 样例

下面是一个样例，
服务地址如下；参数参考下面CCR格式
```
http://132.246.27.77:9100/gw/pm.discount.update
```

输入参数：
```
 {"data":           {
                    "discountMtrUnit": "555",
                    "discountMtrValue": "2",
                    "discountRefCounterType": "1",
					"discountRefItemtype": "10",
                    "discountTariffID": "315168568476361679",
                    "discountType": "2",
                    "discountValue": "555",
                    "effTime": "2018-01-12 10:22:58",
                    "expTime": "2018-01-14 10:22:58",
                    "productID": "2",
                    "tariffName": "22222222",
					"itemID": "1",
                    "tariffType": "5"
}}
```

输出结果：
```
{
                    "data":                     {
                              "discountMtrUnit": "555",
                              "discountMtrValue": "2",
                              "discountRefCounterType": "1",
							  "discountRefItemtype": "10",
                              "discountTariffID": "315168568476361679",
                              "discountType": "2",
                              "discountValue": "555",
                              "effTime": "2018-01-12 10:22:58",
                              "expTime": "2018-01-14 10:22:58",
                              "tariffName": "22222222",
							  "itemID": "1",
                              "tariffType": "5",
                              "updateTime": "2018-01-25 13:12:30"
                    },
                    "msg": "服务调用成功",
                    "retCode": "0" ,
					"discountTariffInfo":           {
                    	"discountMtrUnit": "555",
                    	"discountMtrValue": "2",
                    	"discountRefCounterType": "1",
						"discountRefItemtype": "10",
                    	"discountTariffID": "315168568476361679",
                   		"discountType": "2",
                    	"discountValue": "555",
                    	"effTime": "2018-01-12 10:22:58",
                    	"expTime": "2018-01-14 10:22:58",
                    	"productID": "2",
                    	"tariffName": "22222222",
						"itemID": "1",
                    	"tariffType": "5"
          			}
}
```


