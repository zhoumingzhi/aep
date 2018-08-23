# TierBundleCreate

## 概述

创建产品阶梯资费信息接口(同一产品不允许存在多个阶梯资费或者使用量资费(没有生失效时间重叠判断限制，因为被改的已经没有生失效时间一说))


## 更新历史

 - [20180122 xingxy] 创建本文档。
## 接口规范要求
创建产品阶梯资费信息，并创建阶梯档位表。

## 输入参数

| 编号 | 参数 | 类型 | 名称 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 1 | productID | UTF8String| 产品ID | 是 | |
| 2 | tariffName | UTF8String| 资费名称 | 是 | |
| 3 | tariffType | Integer64| 资费类型 | 是 | 4：阶梯资费|
| 4 | meterType | Integer64| 计量类型 | 是 | |
| 5 | meterUnit | Integer64| 计量单位 | 是 | |
| 6 | meterCycle | Integer64| 计量周期 | 是 | |
| 7 | acctItemID | UTF8String| 账单科目标识 | 是 | |
| 8 | effTime | Time| 生效时间 | 是 | |
| 9 | expTime | Time| 失效时间 | 否 | |
| 10 | tierInfos | Grouped| 详细档位信息 | 是 | （包括index、lowTierValue、highTierValue、tierFee）|
| 11 | lowTierValue | Integer64| 低档值 | 是 | |
| 12 | highTierValue | Integer64| 高档值 | 是 | |
| 13 | tierFee | Integer64| 本档单价 | 是 | |
| 14 | index | Integer64| 本档编号(根据大小排序) | 是 | 根据大小顺序排序档位 |


## 输出结果
| 参数 | 层级 | 类型 | 名称 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- | ---- 
| retCode | 1 | Unsigned32 | 业务级结果代码 | 是 | |
| msg | 1 | UTF8String | 错误描述 | 是 | |
| tierBundleInfo | 1 | Grouped | 阶梯资费明细 | 是 | |
| tierFeeID | 2 | UTF8String | 固定费ID | 是 | |
| tariffName | 2 | UTF8String | 资费名称 | 是 | |
| tariffType | 2 | Integer64 | 资费类型 | 是 | |
| meterType | 2 | Integer64 | 资费类型 | 是 | |
| meterUnit | 2 | Integer64 | 费用 | 是 | |
| meterCycle | 2 | Integer64 | 账单科目标识 | 是 | |
| acctItemID | 2 | UTF8String | 账单科目标识 | 是 | |
| effTime | 2 | Time | 生效时间 | 是 | |
| expTime | 2 | Time | 失效时间 | 是 | |
| createTime | 2 | Time | 创建时间 | 是 | |
| tierInfos | 2 | Grouped | 详细档位信息 | 是 | |
| index | 3 | Integer64 | 本档编号(根据大小排序) | 是 | |
| lowTierValue | 3 | Integer64 | 低档值 | 是 | |
| highTierValue | 3 | Integer64 | 高档值 | 是 | |
| tierFee | 3 | Integer64 | 本档单价 | 是 | |
## 异常
 * 返回相应的信息，并返回代码：core.ok
 
## 样例

下面是一个样例，
服务地址如下；参数参考下面CCR格式
```
http://132.246.27.77:9100/gw/pm.tier.create
```

输入参数：
{
"data":           {
                    "acctItemID": "333",
                    "effTime": "2018-01-12 10:22:58",
                    "expTime": "2018-01-14 10:22:58",
                    "meterCycle": "222",
                    "meterType": "999",
                    "meterUnit": "111",
                    "productID": "315175365575943547",
                    "tariffName": "111",
                    "tariffType": "4",
                    "tierInfos":                     [
                                                            {
                                        "highTierValue": "111",
                                        "index": "1",
                                        "lowTierValue": "0",
                                        "tierFee": "333"
                              },
                                                            {
                                        "highTierValue": "222",
                                        "index": "2",
                                        "lowTierValue": "111",
                                        "tierFee": "666"
                              },
                                                            {
                                        "highTierValue": "333",
                                        "index": "3",
                                        "lowTierValue": "222",
                                        "tierFee": "999"
                              }
                    ]
          }
}
```

输出结果：
```
{
          "data":           {
                    "acctItemID": "333",
                    "effTime": "2018-01-12 10:22:58",
                    "expTime": "2018-01-14 10:22:58",
                    "meterCycle": "222",
                    "meterType": "999",
                    "meterUnit": "111",
                    "productID": "315175365575943547",
                    "tariffName": "111",
                    "tariffType": "4",
                    "tierInfos":                     [
                                                            {
                                        "highTierValue": "111",
                                        "index": "1",
                                        "lowTierValue": "0",
                                        "tierFee": "333"
                              },
                                                            {
                                        "highTierValue": "222",
                                        "index": "2",
                                        "lowTierValue": "111",
                                        "tierFee": "666"
                              },
                                                            {
                                        "highTierValue": "333",
                                        "index": "3",
                                        "lowTierValue": "222",
                                        "tierFee": "999"
                              }
                    ]
          },
          "msg": "服务调用成功",
          "retCode": "0",
          "tierBundleInfo":           {
                    "acctItemID": "333",
                    "effTime": "2018-01-12 10:22:58",
                    "expTime": "2018-01-14 10:22:58",
                    "meterCycle": "222",
                    "meterType": "999",
                    "meterUnit": "111",
                    "tierFeeID": "315175475147690402",
                    "tariffName": "111",
                    "tariffType": "4",
                    "tierInfos":                     [
                                                            {
                                        "highTierValue": "111",
                                        "index": "1",
                                        "lowTierValue": "0",
                                        "tierFee": "333"
                              },
                                                            {
                                        "highTierValue": "222",
                                        "index": "2",
                                        "lowTierValue": "111",
                                        "tierFee": "666"
                              },
                                                            {
                                        "highTierValue": "333",
                                        "index": "3",
                                        "lowTierValue": "222",
                                        "tierFee": "999"
                              }
                    ],
                    "updateTime": "2018-02-02 12:58:34"
          }
}
```



