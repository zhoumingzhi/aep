# DiscountTariffQuery

## 概述

查询产品优惠资费信息接口


## 更新历史

 - [20180122 xingxy] 创建本文档。
## 接口规范要求
查询产品优惠资费信息。

## 输入参数

| 编号 | 参数 | 类型 | 名称 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 1 | itemID | UTF8String| 产品ID | 是 | |


## 输出结果
| 参数 | 层级 | 类型 | 名称 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| retCode | 1 | Unsigned32 | 业务级结果代码 | 是 | |
| msg | 1 | UTF8String | 错误描述 | 是 | |
| discountTariffList | 1 | Grouped | 优惠资费明细 | 是 | |
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
## 异常
 * 返回相应的信息，并返回代码：core.ok
 
## 样例

下面是一个样例，
服务地址如下；参数参考下面格式
```
http://132.246.27.77:9100/gw/pm.discount.query
```

输入参数：
```
{"data":           {
                    "itemID": "2"
          }}
```

输出结果：
```
{
					"discountTariffList": [{
                              "discountMtrUnit": 555,
                              "discountMtrValue": 2,
                              "discountRefCounterType": 1,
							  "discountRefItemtype": "10",
                              "discountTariffID": 3.1516856847636166E17,
                              "discountType": 2,
                              "discountValue": 555,
                              "effTime": "2018-01-12 10:22:58.0",
                              "expTime": "2018-01-14 10:22:58.0",
                              "tariffName": "22222222",
                              "tariffType": 5
                    }],
                    "msg": "服务调用成功",
                    "retCode": "0", 
		 			 "data":           {
                    	"itemID": "2"
          			}
}
```



