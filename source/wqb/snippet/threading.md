---
layout: page
title: 3.多线程编程threading
group: group-snippet
order: 3
sidebar:
  - group-snippet
  - blogger
  - toc
date: 2020-08-09 20:19:27
---
python高级编程之多线程threading  
[官方文档](https://docs.python.org/zh-cn/3/library/threading.html#module-threading, "3.8")
<!-- more -->

## threading线程教程

[官方文档](https://docs.python.org/zh-cn/3/library/threading.html#module-threading, "3.8")

### 简单线程

```python
from threading import Thread

def my_thread(data='default'):
    for i in range(5):
        print(data)
        time.sleep(1)

if __name__ == '__main__':
    thread_01 = Thread(target=my_thread, name='thread_01')  # name自定义线程名称
    thread_02 = Thread(target=my_thread, name='thread_02', args=('undefault',))  # args 使用元组传参，单个参数时需要加 (,) 将自动识别为元组
    print('1.strat...')
    thread_01.start()
    print('2.strat...')
    thread_02.start()
    thread_01.join()  # join作用：主线程等待子线程执行完毕后继续执行，但不阻塞其他子线程运行
    thread_02.join()
    print('ending......')
```

### 线程加锁

```python
from threading import Thread, Lock

lock = Lock()  # Lock() 不能在线程中初始化，要在线程前先初始化

def my_thread(data='default'):
    for i in range(5):
        lock.acquire()
        print(data)
        lock.release()
        time.sleep(1)

if __name__ == '__main__':
    thread_01 = Thread(target=my_thread, name='thread_01')  # name自定义线程名称
    thread_02 = Thread(target=my_thread, name='thread_02', args=('undefault',))  # args 使用元组传参，单个参数时需要加 (,) 将自动识别为元组
    print('1.strat...')
    thread_01.start()
    print('2.strat...')
    thread_02.start()
    thread_01.join()  # join作用：主线程等待子线程执行完毕后继续执行，但不阻塞其他子线程运行
    thread_02.join()
    print('ending......')

###
# 线程加锁前，在控制台打印的日志会有重叠，加锁后解决；
# 锁机制主要用来对操作共享数据的模块前后加锁，实现数据共享而不乱
###
```

### 类线程继承，实现多线程

```python
from threading import Thread, Lock

lock = Lock()  # Lock() 不能在线程中初始化，要在线程前先初始化


def my_thread(data='default'):
    for i in range(5):
        lock.acquire()
        print(data)
        lock.release()
        time.sleep(1)


class MyThread(Thread):
    def __init__(self, data='default'):
        super().__init__()
        self.name = name

    def run(self):
        print(self.ident)
        # lock.acquire()  可在重新run方法中直接加锁
        my_thread(self.name)
        # lock.release()  可在重新run方法中直接解锁


if __name__ == '__main__':
    thread_03 = MyThread()
    thread_04 = MyThread(data='undefault')
    thread_03.start()
    thread_04.start()
    thread_03.join()
    thread_04.join()
    print('ending......')

###
# 类实现线程：1.必须继承threading.Thread类；2.必须重写run方法来实现多线程模块
###
```

<br><br>{% btn large center, 向博主反馈问题, <https://github.com/wongqingbin/blog/issues> , fas fa-paper-plane %}
