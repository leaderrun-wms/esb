# ESB信息架构

参与ESB的系统，包括业务操作系统：

* ASN
* FD
* WMS

和其他对接系统：

* KN
* 后续需要对接的系统
* 业务报表和大数据分析

## 原则

* 通过业务消息产生、传递和存储，作为系统对接的事实依据
* 采用消息队列进行消息的分发传递，业务事件的产生和消费是Pub/Sub模式
* 消息类型尽量以 ```.``` 为分割，能看到业务层级关系，如：
  * ```asn.submitted```
  * ```asn.approved```
  * ```inbound.arrived```
  * ```inbound.receive.started```
  * ```inbound.receive.done```
  * 等
* 消息命名以过去式为准，因为都是记录发生了的事件

### 生产者

* 生产者（系统）产生消息并发送到消息队列
* 生产者可能因为版本升级带来的消息内容格式不兼容问题，在消息里需要包含版本号，以便消费者做兼容性处理
* 生产者在产生特定类型的消息之前，必须在【消息格式库】添加格式定义，以供以后查阅

### 消费者

* 消费者（系统）连接消息队列并过滤它需要的消息，处理后产生自己所需要的数据
* 消费者需要对消息的不同版本进行消息内容的兼容性处理

## 消息报文格式

以JSON格式封装，通用格式包括：

消息头：
* 消息唯一ID（防止消息重复处理）
* 产生系统（ASN/FD/WMS/etc）
* 业务类型
* 报文版本号（针对某个业务类型的报文，采用semver格式）
* 发生时间 (Epoch time in Millisecond)

消息体：
* 按产生系统、业务类型、报文版本号 界定 明确的格式

例如：
```json
{
  "header": {
    "msgId": "12345678XXXXXX",
    "sysId": "ASN",
    "type": "asn.submitted",
    "version": "1.0.0",
    "timestamp": 1592982477000
  },
  "body": {
    // 由不同业务类型产生不同的格式定义，在消息格式注册表查找对应格式
  }
}
```
## 生产者注册表

参考 [生产者注册表](producer-registry) 文件

## 消息格式注册表

参考 [消息格式注册表](message-registry) 文件

## 消费者注册表

参考 [消费者注册表](consumer-registry) 文件
