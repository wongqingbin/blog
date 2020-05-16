![Hexo Deploy CI](https://github.com/wongqingbin/blog/workflows/Hexo%20Deploy%20CI/badge.svg?branch=master&event=push)
![Hexo Deploy CI](https://github.com/wongqingbin/blog/workflows/Hexo%20Deploy%20CI/badge.svg?branch=master&event=repository_dispatch)

https://wongqingbin.github.io/

```YAML
# _conflg.yml
deploy:
  type: git
  repo:
    github: git@github.com:wongqingbin/wongqingbin.github.io.git
    gitee: git@gitee.com:wongqingbin/wongqingbin.git
  branch: master
```

```shell
# hexo部署 hexo clean && hexo deploy
hexo clean
hexo generate
hexo deploy
# hexo g -d
```
<br>

### 免费图床
 - github
 - cdn.jsdelivr.net
 - gitee
 - PicGo
