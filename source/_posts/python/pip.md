---
title: pip修改源
tags: pip
categories: python
date: 2020-08-08 18:59:54
---
pip修改国内源
<!-- more -->

```bash
# 1. 临时使用源
pip install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple --trusted-host pypi.tuna.tsinghua.edu.cn
# 清华维护：https://pypi.tuna.tsinghua.edu.cn/simple
```

```text
# 2. 可选国内源列表
阿里云
http://mirrors.aliyun.com/pypi/simple/

中国科技大学
https://pypi.mirrors.ustc.edu.cn/simple/

豆瓣(douban)
http://pypi.douban.com/simple/

清华大学
https://pypi.tuna.tsinghua.edu.cn/simple/

中国科学技术大学
http://pypi.mirrors.ustc.edu.cn/simple/
```

<br><br>{% btn large center, 向博主反馈问题, <https://github.com/wongqingbin/blog/issues> , fas fa-paper-plane %}
