---
title: Python中的异常处理问题
tags: Exception
categories: python
date: 2020-06-10 23:00:18
---
Python不同于其他语言的异常处理之超级优雅的方式
<!-- more -->

## 优雅的异常处理

```python
try:
    print('这是要监控执行的代码块')
except A:
    print('A类型异常时执行此处')
except B:
    print('B类型异常时执行此处')
except:
    print('其他类型异常时执行此处')
else:
    print('try监控的代码块无异常时执行此处')
finally:
    print('无论try代码块是否有异常均执行此处')
```

<br><br>{% btn large center, 向博主反馈问题, <https://github.com/wongqingbin/blog/issues> , fas fa-paper-plane %}
