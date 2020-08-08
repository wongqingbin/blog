---
title: npm更换国内源
tags: npm
categories: vue
date: 2020-08-08 19:12:47
---
npm更换阿里源
<!-- more -->

```bash
# 查看npm的地址源
npm config get registry  # 或 npm info express
# 修改npm的地址源为淘宝源 无需安装cnpm
npm config set registry https://registry.npm.taobao.org --global
```

```bash
# 安装cnpm,cnpm默认使用淘宝源
npm install -g cnpm --registry=http://registry.npm.taobao.org
```

<br><br>{% btn large center, 向博主反馈问题, <https://github.com/wongqingbin/blog/issues> , fas fa-paper-plane %}
