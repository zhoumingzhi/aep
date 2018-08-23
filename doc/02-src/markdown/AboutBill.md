# 总流程

 计费总流程步骤为：
 1. 先实时累账(`bill.real.xml`)
 2. 固定费用计算(`bill.fix.batch.xml`)
 3. 资费套餐计算(`bill.discount.batch.xml`)
 4. 出账(`bill.output.batch.xml`)
 5. 月结（`bill.writeoff.batch.xml`）

 每个步骤mr工作目录都类似，比如

 * 实时累账目录为`${vfs.homoe}=${vfs.root}/${vfs.working}/bill/real`
 * 一次性计算目录为`${vfs.homoe}=${vfs.root}/${vfs.working}/bill/oneTime`
 * 优惠计算目录为`${vfs.homoe}=${vfs.root}/${vfs.working}/bill/discount`
 * 出账费用计算目录为 `${vfs.homoe}=${vfs.root}/${vfs.working}/bill/output`
 * 出账费用计算目录为 `${vfs.homoe}=${vfs.root}/${vfs.working}/bill/writeoff`
 `${vfs.root}/${vfs.working}`这两个变量配置在工程的setting.xml文件中。其中`${vfs.root}=/apps` `${vfs.working}=alogic/aepdata/data`。

# 详细流程

1. 首先实时累账（`bill.real.xml`).每5分钟执行一次，脚本先从晓云的的计量目录下
`/apps/alogic/aepdata/data/mergebill`。 将计量文件移到实时累账的输入目录`${vfs.home}/${day}/${$task}/in`
再利用`check-file`插件检查清单是否存在清单查重表`JF_DETAIL_REPEAT`中，如果已经存在，则将此文件移到
`${vfs.home}/${day}/${$task}/hup`目录下面。然后在开始启动mr。先从实例表`PROD_INST`中找订购信息，从套餐资费
表`PM_PROD_TARIFF`中找资费(使用量资费或者阶梯计费，这两个套餐互斥），将实时累积量插入到累积量表`JF_COUNTER`。按
照套餐中资费批价，将批价值写入计费表`IB_FEE`中`real_amt`字段.批价出来话单放`${vfs.home}/${day}/${$task}/out`
2. 然后是月初固定费计算（`bill.onetime.batch.xml`）.同样是先从实例表`PROD_INST`中找订购信息，在从套餐资费表`PM_PROD_TARIFF`中找固定资费，再找固定资费`PM_FIX_BUNDLE`，
计算出来的值放入到计费表`IB_FEE`中`onetime_amt`。
3. 接着是月初的资费优惠计算（`bill.discount.batch.xml`). 同样是先从实例表`PROD_INST`中找订购信息，在从套餐
资费表`PM_PROD_TARIFF`中找优惠资费，在找优惠资费表`PM_DISCOUNT_TARIFF`，优惠有两种类型,一种是
`discount_type=1`，打折优惠，对`IB_FEE`中`real_amt`和`onetime_amt`累加值进行优惠。将优惠值填入`discount_amt`字段。`discount_type=2`，扣减优惠，同样对`IB_FEE`中`real_amt`和`onetime_amt`累加值进行优惠,将优惠值填入`discount_amt`字段,`discount_amt`为负值。
4. 最后是月初的出账(`bill.output.batch.xml`)。出账有两部分，一是上述流程产生的`IB_FEE`中记录到账单表
`IB_BILL`。二是，crm订单竣工产生的`IB_PRODINS_FEE`的crm订单费用。第一部分是将`IB_FEE`中的`real_amt`,`onetime_amt`,`discount_amt`三个字段相加 ，按照客户custId、账户acctId、账单科目acctItemId，产品prodId进行合并，并查找账单科目表`IB_ACCT_TYPE`中的税
率，将计算出来的值插入到账单表`IB_BILL`。第二部分是根据crm订购实例的生失效时期计算本订购记录在本账期产生的费用
，同时根据`IB_ACCT_TYPE_PROD`中查找订购类型prod_type关联的账目和税率，计算出来值同样插入到账单表中`IB_BILL`。

# 联调环境如何测试：

1. 登录132.246.27.76联调机子，cd 到/home/alogic/ngbilling/lib 目录
2. 执行`../bin/ng-billing-cmd.sh event=bill.real`脚本，看下清单查重表`JF_DETAIL_REPEAT`是否有相应的文件。
看下积量表`JF_COUNTER`中是否生成数据，其中`counter_type=1`是按照消息，`counter_type=2`是按照次数。
去订购实例`prod_inst`中找租户的订购信息，再到资费套餐表`pm_prod_tariff`中找使用量资费或者阶梯资费，当资费表中的
`meter_type`和清单记录中一样时，才可以进行批价。
3. 接着执行脚本`../bin/ng-billing-cmd.sh event=bill.onetime.batch` 执行一次性资费计算。
4. 然后是执行`../bin/ng-billing-cmd.sh event=bill.dicount.batch` 。执行优惠计算。逻辑是根据订购实例找到优
惠资费表`pm_discount_tariff`，对费用表`IB_FEE`进行优惠
5. 最后执行`../bin/ng-billing-cmd.sh event=bill.output.batch` 。执行出账，对`IB_FEE`中数据按照custId,acctId,acctItemId,billCycleId,prodId进行累账
6. 销账执行`../bin/ng-billing-cmd.sh event=bill.writeoff.batch`. 先遍历账户表`cm_ca_account`，对每个账户进行销账，发现余额表`ib_balance`该账户有余额时，就对他进行销账，余额减少并将相关记录写到余额变更表`ib_balance_chglog`中。
7. 外部收费账单下发`../bin/ng-billing-cmd.sh event=bill.branch.bss`。先扫描客户表，捞出
`channel='crm'`外部收费客户。执行mr,到账单表`IB_BILL`捞取状态还未收的外部客户的账单，按照指定的格式生成二进制格式的账单文件和账单稽核文件。下放BSS收费目录为`/apps/alogic/aepdata/data/billtoiot`

# 生成环境如何登陆

- 登陆生产跳转机 180.106.150.186 udal/udal#123 然后在跳转到192.168.73.101  alogic/Ab123456!
