#  acct.bill.info

## 概述

5.8.2 账户总览信息查询
关联的数据表有 余额表IB_BALANCE、欠费表IB_CB_UNWOFFCUST、发票索取表CM_RLIST_INFO、计费表IB_FEE

## 更新历史
 - [20180731 chenjiadong] 添加实时费用。

## 接口规范要求

指定custID查询账户相关信息。

## 输入参数

| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
| 1 | custID | Long| 是 | 客户ID|


## 输出结果
| 编号 | 参数 | 类型 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- |
| 1 | retCode | String| 必填 | 0 表示成功，其他值则为错误代码 |
| 2 | msg | String| 可选 | 提示信息 |
| 3| amt | Long|必填 | 账户余额 |
| 4| unwoffAMT | Long|必填 | 账户未结清金额 |
| 5| receiptAMT | Long|必填 | 可索取发票总额 |
| 6| realamt | Long|必填 | 实时费用 |


## 异常
 * 返回相应的信息，并返回代码：core.ok
 
## 样例

下面是一个样例，
```
Enterprise/CustomerMag/AccountOverviewInfoQuery
```

输入参数：
```
输入AcctID按帐户查询
{
	"data": {
		"custID": "111"
	}
}
```

输出结果：
```
{
	"msg": "服务调用成功",
	"retCode": "0",
	"unwoffAMT": "232",
	"amt": "234",
	"realamt":321
	"receiptAMT": "24"	
}
```



