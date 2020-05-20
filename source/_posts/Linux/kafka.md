---
title: CentOS 7 安装 kafka
tags: kafka
categories: Linux
date: 2020-05-20 22:27:38
---
CentOS 7 安装 kafka，简单配置使用kafka
<!-- more -->

## 安装
```bash
# 下载安装包
wget http://mirror.bit.edu.cn/apache/kafka/2.2.0/kafka_2.12-2.2.0.tgz
# 解压安装包
tar -xzf kafka_2.12-2.2.0.tgz
```

## 启动
```bash
# 启动zookeeper
bin/zookeeper-server-start.sh config/zookeeper.properties
# 启动kafka
bin/kafka-server-start.sh config/server.properties
```

## 测试
```bash
# 创建topic
bin/kafka-topics.sh --create --bootstrap-server localhost:9092 -- replication-factor 1 --partitions 1 --topic test
# 列出topic
bin/kafka-topics.sh --list --bootstrap-server localhost:9092
# 发送消息
bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test
# 接收消息
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 -- topic test --from-beginning
```


<br><br>{% btn large center, 向博主反馈问题, https://github.com/wongqingbin/blog/issues , fas fa-paper-plane %}