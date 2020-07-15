# KN对接：消费者实现

## 通用结构

样本：

```json
{
    "statusCode":1,
    "status": "Start",
    "operatingTime": "2019-05-20 12:12:10",
    "physnd":" KNLGP02 ",
    "logsnd":" HKHKG01 ",
    "inn":" HKGS66113479",
    "refNo": "4363-0870-905.029",
    "customerLinkedMan":" HKG EE/TERRENCE WONG",
    "email":" TERRENCE.WONG@KUEHNE-NAGEL.COM",
    "company": " Leaderrun",
    "remark": "A ASNNO",
    "statusloc": " HKHKG "
}
```

报文定义：

| 字段              | 类型     | 说明 | 必填 | 备注                                                          |
| ----------------- | -------- | ---- | ---- | ------------------------------------------------------------- |
| statusCode        | String   |      | 是   | 见下表                                                        |
| status            | String   |      | 是   | 见下表                                                        |
| operatingTime     | DateTime |      | 是   | 格式:yyyy-MM-dd HH:mm:ss                                      |
| physnd            | String   |      | 是   | KNLOBI/MSGHDR/PHYSND节点值                                    |
| logsnd            | String   |      | 是   | KNLOBI/MSGHDR/HKHKG01节点值                                   |
| inn               | String   |      | 是   | KNLOBI/S/MSGLVL/REF/CDE为INN时，取VAL节点值                   |
| refNo             | String   |      | 是   |                                                               |
| customerLinkedMan | String   |      | 是   | KNLOBI/S/SHPINF/NADINF[ADDTYP=“FF”]/CTA/NAD                   |
| email             | String   |      | 是   | KNLOBI/S/SHPINF/NADINF[ADDTYP=“FF”]/CTA/COM[COMTYP=”EM”]      |
| company           | String   |      | 是   | 固定值：Leaderrun                                             |
| remark            | String   |      | 是   | 标注对应SO按包装单位汇总的收货数量及包装单位（CTN/PLT）和柜号 |
| statusloc         | String   |      | 是   | 取字段logsnd值的头五位                                        |


状态定义；

| 序号 | statusCode | status              | 说明                    | 备注 |
| ---- | ---------- | ------------------- | ----------------------- | ---- |
| 1    | 1          | Started             | 报关开始                |      |
| 2    | 2          | Passed              | 报关放行                |      |
| 3    | 3          | Check               | 报关查检                |      |
| 4    | 4          | received complete   | 收货数量与ASN数量一致   |      |
| 5    | 5          | received incomplete | 收货数量与ASN数量不一致 |      |
| 6    | 6          | loaded              | 装柜完成                |      |