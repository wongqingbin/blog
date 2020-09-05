---
layout: page
title: 5.SQLAlchemy
group: group-snippet
order: 5
sidebar:
  - group-snippet
  - blogger
  - toc
date: 2020-09-06 01:11:52
---
python3使用SQLAlchemy对mysql数据类型的映射关系表
<!-- more -->

## 数据类型关系表

| 类型名 | MySQL类型 | python类型 | 描述 |
| ---   |---       |---         |---  |
SmallInteger | smallint | int | 取值范围较小，一般为16位
Integer | int | int | 普通整数，一般32位
BigInteger | bigint | int/long | 不限精度的整数
Float | float | float | 浮点数
Numeric | decimal | decimal.Decimal | 定点数
String | varchar | str | 变长字符串
Text | tinytext | str | 变长字符串，64K
Text(65536) | mediumtext | str | 变长字符串，max16M
Text(16777216) | longtext | str | 变长字符串，max32M
LargeBinary | blob | str | 二进制文件，64K
LargeBinary(65536) | mediumblob | str | 二进制，max16M
LargeBinary(16777216) | longblob | str | 二进制，max32M
PickleType | blob | 任何python对象 | 自动使用Pickle序列化，只有blob，存json数据
Unicode | varchar | unicode | 变长字符串
UnicodeText | text | unicode | 变长字符串，64K
Boolean | tinyint | bool | 布尔值
Date | date | datetime.date | 日期
Time | time | date.time | 时间
DateTime | datetime | datetime.datetime | 日期和时间
Interval | datetime | datetime.timedelta | 时间间隔
Enum | enum | str | 一组字符串

## 字段设置对照表

| 属性 | 描述 | 生效值 |
| :---: | :---: | :---: |
| primary_key | 主键 | True |
| unique | 键值唯一性 | True |
| index | 索引 | True |
| nullable | 空值 | True |
| default | 默认值 | null |

## python代码示例

```python
class Data(db.Model):
    __tablename__ = "datas"
    id = db.Column(db.Integer, primary_key=True)
    smallInteger = db.Column(db.SmallInteger)
    bigInteger = db.Column(db.BigInteger)
    floatData = db.Column(db.Float(10))
    numericData = db.Column(db.Numeric(10))
    stringData = db.Column(db.String(250))
    textData = db.Column(db.Text(200))
    mediumText = db.Column(db.Text(65536))
    longText = db.Column(db.Text(16777216))
    largeBinary = db.Column(db.LargeBinary(300))
    mediumBlob = db.Column(db.LargeBinary(65536))
    longBlob = db.Column(db.LargeBinary(16777216))
    pickle = db.Column(db.PickleType)
    mediumPickle = db.Column(db.PickleType(65536))
    longPickle = db.Column(db.PickleType(16777216))
    unicodeData = db.Column(db.Unicode(10))
    unicodeText = db.Column(db.UnicodeText)
    booleanData = db.Column(db.Boolean(0))
    dateData = db.Column(db.Date)
    timeData = db.Column(db.Time)
    dateTime = db.Column(db.DateTime)
    interval = db.Column(db.Interval)
    enumData = db.Column(db.Enum('father', 'mother'))

    def __repr__(self):
        return "Data {}".format(self.id)
```
