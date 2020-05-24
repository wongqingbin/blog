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

```bash
# hexo部署 hexo clean && hexo deploy
hexo clean
hexo generate
hexo deploy
# hexo g -d
```

```bash
# 新建文章
hexo new post -p mac/Finder "Finder"
# post: 建立post类型模板的文章，source/_post为默认主目录，可省略不写
# -p --path: 指定路径和文件名称 mac/ 路径，Finder为.md名称
# "Finder": 文章标题title

# 新建页面
hexo new page -p about/me "about me"
# source/ 为主目录，page不可省略
```
<br>

### 免费图床
 - github
 - cdn.jsdelivr.net
 - gitee
 - PicGo
 - 博主个人图床地址：https://github.com/wongqingbin/PicGo
 - 博主个人图床地址(国内)：https://gitee.com/wongqingbin/Frieza
 
### 使用开源项目申请jetbrains的免费linces
 - https://www.jetbrains.com/shop/eform/opensource?product=ALL
