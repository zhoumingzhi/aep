# UsageBundleUpdate

## 概述

更新产品使用量资费信息接口(同一产品不允许存在多个阶梯资费或者使用量资费(没有生失效时间重叠判断限制，因为被改的已经没有生失效时间一说))


## 更新历史

 - [20180122 xingxy] 创建本文档。
## 接口规范要求
更新产品使用量资费信息。

## 输入参数

| 编号 | 参数 | 类型 | 名称 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 1 | usageFeeID | UTF8String| 使用量资费ID | 是 | |
| 2 | tariffName | UTF8String| 资费名称 | 是 | |
| 3 | tariffType | Integer64| 资费类型 | 是 | 3：使用量资费|
| 4 | meterValue | Integer64| 计量值 | 是 | |
| 5 | meterType | Integer64| 计量类型 | 是 | |
| 6 | meterUnit | Integer64| 计量单位 | 是 | |
| 7 | meterCycle | Integer64| 计费周期 | 是 | |
| 8 | acctItemID | Enumerated| 账单科目标识 | 是 | |
| 9 | effTime | Time| 生效时间 | 是 | |
| 10 | expTime | Time| 失效时间 | 否 | |


## 输出结果
| 参数 | 层级 | 类型 | 名称 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| retCode | 1 | Unsigned32 | 业务级结果代码 | 是 | |
| msg | 1 | UTF8String | 错误描述 | 是 | |
| usageBundleInfo | 1 | Grouped | 使用量资费明细 | 是 | |
| usageFeeID | 2 | UTF8String | 使用量资费ID | 是 | |
| tariffName | 2 | UTF8String | 资费名称 | 是 | |
| tariffType | 2 | Integer64 | 资费类型 | 是 | |
| meterValue | 2 | Integer64 | 计量值 | 是 | |
| meterType | 2 | Integer64 | 计量类型 | 是 | |
| meterUnit | 2 | Integer64 | 计量单位 | 是 | |
| meterCycle | 2 | Integer64 | 计费周期 | 是 | |
| acctItemID | 2 | UTF8String | 账单科目标识 | 是 | |
| effTime | 2 | Time | 生效时间 | 是 | |
| expTime | 2 | Time | 失效时间 | 是 | |
| updateTime | 2 | Time | 创建时间 | 是 | |
## 异常
 * 返回相应的信息，并返回代码：core.ok
 
## 样例

下面是一个样例，
服务地址如下；参数参考下面CCR格式
```
http://132.246.27.77:9100/gw/pm.usage.update
```

输入参数：
```
{"data":           {
                    "acctItemID": "777",
                    "effTime": "2018-01-12 10:22:58",
                    "expTime": "2018-01-14 10:22:58",
                    "meterCycle": "666",
                    "meterType": "444",
                    "meterUnit": "555",
                    "meterValue": "333",
                    "tariffName": "111111111111",
                    "tariffType": "3",
                    "usageFeeID": "111"
}}
```

输出结果：
```
{
                    "msg": "服务调用成功",
                    "retCode": "0",
                    "usageBundleInfo":                     {
                              "acctItemID": "777",
                              "effTime": "2018-01-12 10:22:58",
                              "expTime": "2018-01-14 10:22:58",
                              "meterCycle": "666",
                              "meterType": "444",
                              "meterUnit": "555",
                              "meterValue": "333",
                              "tariffName": "111111111111",
                              "tariffType": "3",
                              "updateTime": "2018-01-25 15:12:32",
                              "usageFeeID": "111"
                    },
          			"data":           {
                    	"acctItemID": "777",
                    	"effTime": "2018-01-12 10:22:58",
                    	"expTime": "2018-01-14 10:22:58",
                    	"meterCycle": "666",
                    	"meterType": "444",
                    	"meterUnit": "555",
                    	"meterValue": "333",
                    	"tariffName": "111111111111",
                    	"tariffType": "3",
                    	"usageFeeID": "111"
          			}
}
```



