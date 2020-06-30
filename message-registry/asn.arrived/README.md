# asn.arrived (ASN到达仓库：接单)

## 消息体格式

| 字段          | 描述     | 样本          |
|---------------|----------|---------------|
| asn           | ASN号码  | ASN2006001234 |
| warehouseCode | 仓库代码 | PLA           |
| arrivedAt     | 到达时间 | 1592982477000 |

## 样本

```json
{
    "asn": "ASN2006001234",
    "warehouseCode": "PLA",
    "arrivedAt": 1592982477000
}
```
