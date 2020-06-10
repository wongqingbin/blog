---
title: git rebase
tags: git
categories: Git
date: 2020-06-10 22:10:42
---
git管理代码库之git rebase变基，让代码提交历史更加清晰明了，使git log提交为一条线
<!-- more -->
## 基础用法

```bash
# dev分支合并前先变基
dev> git rebase master
# 如果遇到冲突，则解决完冲突后继续执行未完成的变基
dev> git rebase --continue
# 变基完成后，切换到master分支
dev> git checkout master
# master合并merge变基后的dev分支
master> git merge dev
# master分支提交代码
master> git push
# 切换回开发分支
master> git checkout dev
dev>
```

<br><br>{% btn large center, 向博主反馈问题, <https://github.com/wongqingbin/blog/issues> , fas fa-paper-plane %}
