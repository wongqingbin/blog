---
title: 回滚版本号
tags: git
categories: Git
date: 2020-08-10 23:21:38
---
git回退版本并强制提交至远程仓库
<!-- more -->
```bash
# 本地回退命令
git reset --hard HEAD^         # 回退到上个版本
git reset --hard HEAD~3        # 回退到前3次提交之前，以此类推，回退到n次提交之前
git reset --hard commit_id     # 退到/进到 指定commit的sha码(git log查看commit)

# 强推推送到远程仓库
git push origin HEAD --force
```

<br><br>{% btn large center, 向博主反馈问题, <https://github.com/wongqingbin/blog/issues> , fas fa-paper-plane %}
