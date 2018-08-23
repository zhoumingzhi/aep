# TierBundleQuery

## 概述

查询产品阶梯资费信息接口


## 更新历史

 - [20180122 xingxy] 创建本文档。
## 接口规范要求
查询产品阶梯资费信息，关联查询阶梯资费档位信息(以数组形式输出)。

## 输入参数

| 编号 | 参数 | 类型 | 名称 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 1 | productID | UTF8String| 产品ID | 是 | |


## 输出结果
| 参数 | 层级 | 类型 | 名称 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| retCode | 1 | Unsigned32 | 业务级结果代码 | 是 | |
| msg | 1 | UTF8String | 错误描述 | 是 | |
| tierBundleList | 1 | Grouped | 阶梯资费明细 | 是 | |
| tierFeeID | 2 | UTF8String | 阶梯资费ID | 是 | |
| tariffName | 2 | UTF8String | 资费名称 | 是 | |
| tariffType | 2 | Integer64 | 资费类型 | 是 | |
| meterType | 2 | Integer64 | 计量类型 | 是 | |
| meterUnit | 2 | Integer64 | 计量单位 | 是 | |
| meterCycle | 2 | Integer64 | 计量周期 | 是 | |
| acctItemID | 2 | UTF8String | 账单科目标识 | 是 | |
| effTime | 2 | Time | 生效时间 | 是 | |
| expTime | 2 | Time | 失效时间 | 是 | |
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
http://132.246.27.77:9100/gw/pm.tier.query
```

输入参数：
```
{"data": {"productID": "315175365575943547"}}
```

输出结果：
```
{
          "data": {"productID": "315175365575943547"},
          "msg": "服务调用成功",
          "retCode": "0",
          "tierBundleList": [          {
                    "acctItemID": "1",
                    "effTime": "2018-02-01 00:00:00.0",
                    "expTime": "2018-03-31 00:00:00.0",
                    "meterCycle": "1",
                    "meterType": "10",
                    "meterUnit": "100",
                    "tariffName": "123",
                    "tariffType": "1",
                    "tierFeeID": "315175471556224411",
                    "tierInfos":                     [
                                                            {
                                        "highTierValue": "100",
                                        "index": "1",
                                        "lowTierValue": "0",
                                        "tierFee": "1"
                              },
                                                            {
                                        "highTierValue": "500",
                                        "index": "2",
                                        "lowTierValue": "100",
                                        "tierFee": "2"
                              }
                    ]
          }]
}
```



