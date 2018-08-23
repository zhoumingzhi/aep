# OneTimeFeeUpdate

## 概述

更新产品一次性资费信息接口


## 更新历史

 - [20180122 xingxy] 创建本文档。
## 接口规范要求
更新产品一次性资费信息。

## 输入参数

| 编号 | 参数 | 类型 | 名称 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 1 | onetimeFeeID | UTF8String| 一次性资费ID | 是 | |
| 2 | tariffName | UTF8String| 资费名称 | 是 | |
| 3 | tariffType | Integer64| 资费类型 | 是 | 1：一次性资费|
| 4 | fee | Integer64| 费用 | 是 | |
| 5 | acctItemID | UTF8String| 账单科目标识 | 是 | |
| 6 | effTime | Time| 生效时间 | 是 | |
| 7 | expTime | Time| 失效时间 | 否 | |
| 8 | chargingMode | UTF8String | 收费模式 | 是 | 0：一次性收费，1：按月收费 |


## 输出结果
| 参数 | 层级 | 类型 | 名称 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| retCode | 1 | Unsigned32 | 业务级结果代码 | 是 | |
| msg | 1 | UTF8String | 错误描述 | 是 | |
| oneTimeFeeInfo | 1 | Grouped | 一次性资费明细 | 是 | |
| onetimeFeeID | 2 | UTF8String | 一次性资费ID | 是 | |
| tariffName | 2 | UTF8String | 资费名称 | 是 | |
| tariffType | 2 | Integer64 | 资费类型 | 是 | |
| fee | 2 | Integer64 | 费用 | 是 | |
| acctItemID | 2 | UTF8String | 账单科目标识 | 是 | |
| chargingMode | 2 | UTF8String | 收费模式 | 是 | |
| effTime | 2 | Time | 生效时间 | 是 | |
| expTime | 2 | Time | 失效时间 | 是 | |
| updateTime | 2 | Time | 创建时间 | 是 | |
## 异常
 * 返回相应的信息，并返回代码：core.ok
 
## 样例

下面是一个样例，
服务地址如下；参数参考下面CCR格式
```
http://132.246.27.77:9100/gw/pm.onetime.update
```

输入参数：
```
{"data":           {
                    "acctItemID": "444",
                    "effTime": "2018-01-12 10:22:58",
                    "expTime": "2018-01-14 10:22:58",
                    "fee": "333",
                    "onetimeFeeID": "111",
                    "tariffName": "111111111111",
					"chargingMode": "0",
                    "tariffType": "1"
}}
```

输出结果：
```
{
                    "msg": "服务调用成功",
                    "oneTimeFeeInfo":                     {
                              "acctItemID": "444",
                              "effTime": "2018-01-12 10:22:58",
                              "expTime": "2018-01-14 10:22:58",
                              "fee": "333",
                              "onetimeFeeID": "111",
                              "tariffName": "111111111111",
							  "chargingMode": "0",
                              "tariffType": "1",
                              "updateTime": "2018-01-25 14:57:14"
                    },
                    "retCode": "0" ,
          			"data":           {
                    	"acctItemID": "444",
                    	"effTime": "2018-01-12 10:22:58",
                    	"expTime": "2018-01-14 10:22:58",
                    	"fee": "333",
                    	"onetimeFeeID": "111",
                    	"tariffName": "111111111111",
						"chargingMode": "0",
                    	"tariffType": "1"
          		}
}
```



