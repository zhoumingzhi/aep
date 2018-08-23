#  recharge

## 概述

前端点击传入账单表的返销参数，后端将缴费重新退回到余额表

## 更新历史

 - [20180522  zhoumingzhi] 创建本文档。

 ## 输入参数
 
| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|custId|varchar|必填|客户|
|3|Id|varchar|必填|欠费表IB_CB_UNWOFFCUST或者已完全销账表IB_CB_WOFFCUST的记录主键Id|
 
## 输出参数
 
| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
|1|retcode|String|必填|0表示成功，其他值表示错误代码|
|2|msg|String|可选|提示信息|

## 样例

下面是一个样例，
```
/Enterprise/AcctMag/pay/IBbackCharge
```






