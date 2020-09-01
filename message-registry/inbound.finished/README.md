# inbound.finished (入仓卸货)

## 消息体格式

| 字段           | 描述              | 样本             |
|----------------|------------------|---------------   |
| orderNumber    | 入库单号          | IPLA200300001   |
| customerCode   | 收货方代码        | KN-ACCO         |
| storageDate    | 收货日期          |2020-06-05       |
| soInfos        | SO入仓信息        |list             |
| soCode         |  SO              |4363-9188-001.123|
| packs          | 包装信息          |list             |
| unit           | 包装单位          |CTN / PLT        |
| packageQty     | 包装数量          | 56              |
| inboundType    | 收货模式          | PDA / 导入      |


## 样本

```json
{
    "orderNumber": "IPLA200300001",
    "customerCode": "KN-ACCO",
    "storageDate": "2020-06-05",
    "soInfos":[{
        "soCode": "4363-9188-001.123",
        "packs":[
            {unit:"PLT","packageQty":"5"},
            {unit:"CTN","packageQty":"3"}
        ]
    }],
    "inboundType": "PDA"
}
```
