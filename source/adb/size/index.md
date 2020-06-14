---
layout: page
title: 获取设备分辨率
date: 2020-06-14 19:05:42
group: group-adb
order: 6
sidebar: [group-adb, blogger, toc]
---

## 获取分辨率

```bash
adb shell wm size
# or
adb shell "dumpsys window | grep mUnrestrictedScreen"
```
