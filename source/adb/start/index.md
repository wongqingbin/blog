---
layout: page
title: 获取apk启动类类名
date: 2020-06-14 19:00:22
group: group-adb
order: 5
sidebar: [group-adb, blogger, toc]
---

## 获取APP启动类名

```bash
# 1. 手机启动APP，然后输入一下命令获取当前运行APP的类名
adb shell dumpsys activity | grep "mFocusedActivity"

# 2 从日志中获取
adb shell logcat *:S ActivityManager:V
```
