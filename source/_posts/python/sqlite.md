---
title: python封装sqlite3
tags: sqlite3
categories: python
date: 2020-08-08 18:38:01
---
python3使用Sqlite3本地数据库存储数据
<!-- more -->

```python
import sqlite3


def dict_factory(cursor, row):
    d = {}
    for idx, col in enumerate(cursor.description):
        d[col[0]] = row[idx]
    return d


class Demo(object):

    def __init__(self):
        super(Demo, self).__init__()
        self.conn = sqlite3.connect('test.db')

    def create(self):
        with self.conn:
            self.conn.execute('''CREATE TABLE COMPANY
               (ID INT PRIMARY KEY     NOT NULL,
               NAME           TEXT    NOT NULL,
               AGE            INT     NOT NULL,
               ADDRESS        CHAR(50),
               SALARY         REAL);'''
            )

    def insert(self):
        with self.conn:
            self.conn.execute("INSERT INTO COMPANY (ID,NAME,AGE,ADDRESS,SALARY) \
               VALUES (5, 'Paul', 32, 'California', 20000.00 )")

    def select(self):
        self.conn.row_factory = dict_factory  # 查询数据结果返回为字典：[{},{}]
        c = self.conn.cursor()
        c.execute("SELECT id, name, address, salary  from COMPANY")
        print(c.fetchall())  # [{key: value, key: value}, {...}, {...}]
        print(c.fetchone())  # [{key: value, key: value}]
        return c.fetchall()  # List[Dict]

    def update(self):
        with self.conn:
            self.conn.execute("UPDATE COMPANY set SALARY = 25000.00 where ID=1")

    def delete(self):
        with self.conn:
            self.conn.execute("DELETE from COMPANY where ID=2;")

    def __del__(self):
        self.conn.close()


if __name__ == '__main__':
    obj = Demo()
    # obj.create()
    # obj.insert()
    obj.select()
    # obj.update()
    # obj.delete()
```

<br><br>{% btn large center, 向博主反馈问题, <https://github.com/wongqingbin/blog/issues> , fas fa-paper-plane %}
