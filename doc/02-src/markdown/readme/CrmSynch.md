# CrmSynch

## 概述

CRM资料同步


## 更新历史

 - [20180719 xingxy] 创建本文档。
## 接口规范要求
CRM资料同步

## 输入参数

| 编号 | 参数 | 类型 | 名称 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| 1 | contractRoot | UTF8String| 资料报文 | 是 | json |

## 输出结果
| 参数 | 层级 | 类型 | 名称 | 是否必须 |说明 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| retCode | 1 | Unsigned32 | 业务级结果代码 | 是 | 0表示调用执行成功 |
| msg | 1 | UTF8String | 返回结果 | 是 | |
| contractRoot | 1 | Unsigned32 | 应答 | 是 | |
| svcCont | 2 | Unsigned32 |  | 是 | |
| tcpCont | 2 | Unsigned32 | 应答消息 | 是 | |
| transactionID | 3 | Unsigned32 | 事务id | 是 | |
| customerOrderId | 3 | Unsigned32 | 订单id | 是 | |
| rspTime | 3 | Unsigned32 | 应答时间 | 是 | |
| response | 3 | Unsigned32 | 应答内容 | 是 | |
| rspCode | 4 | Unsigned32 | 应答编号 | 是 | “0000”表示成功，“0001”表示失败 |
| rspDesc | 4 | Unsigned32 | 应答内容 | 是 | “操作成功”或者错误原因 |

## 异常
 * 返回相应的信息，并返回代码：core.ok
 
## 样例

下面是一个样例，
服务地址如下；参数参考下面CCR格式
```
http://132.246.27.77:20010/gw/crm.synch
```

输入参数：
```
{
	报文资料
}
```

输出结果：
```
{
	"msg": "服务调用成功",
	"retCode": "0" ,
   	"msg": "json报文",
 "contractRoot": {
    "svcCont": {
    },
    "tcpCont": {
      "response": {
        "rspCode": "0000",
        "rspDesc": "操作成功"
      },
      "customerOrderId": "27701923",
      "rspTime": "20180731160726",
      "actionCode": "1",
      "transactionID": "277019231000845991"
    }
	
}

```



