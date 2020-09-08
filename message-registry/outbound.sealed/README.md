# outbound.sealed (出仓卸货)

## 消息体格式

| 字段           | 描述              | 样本            |
|----------------|------------------ |---------------  |
| orderNumber    | 出库库单号        |XPLAH200700417   |
| containerNumber| 柜号              | KDA-UUU-99      |
| outboundDate   | 装柜完成日期       |2020-06-05       |
| soInfos        | SO出库信息        |list             |
| soCode         | SO               |4363-9188-001.123|
| packs          | 包装信息          |list             |
| unit           | 包装单位          |PCS / CTN / PLT  |
| qty            | 包装数量          | 56              |



## 样本

```json
{
    "orderNumber": "XPLAH200700417",
    "containerNumber": "KDA-UUU-99",
    "outboundDate": "2020-06-05",
    "soInfos": [
      {
        "soCode": "4363-0923-912.011A",
        "packs": [
          {
            "unit": "PLT",
            "qty": "1"
          },
          {
            "unit": "CTN",
            "qty": "2"
          }
        ]
      },
      {
        "soCode": "4363-0923-912.011B",
        "packs": [
          {
            "unit": "PLT",
            "qty": "3"
          },
          {
            "unit": "CTN",
            "qty": "4"
          }
        ]
      },
      {
        "soCode": "4363-9188-001.122",
        "packs": [
          {
            "unit": "PLT",
            "qty": "5"
          },
          {
            "unit": "CTN",
            "qty": "6"
          }
        ]
      }
    ]
  }
```
