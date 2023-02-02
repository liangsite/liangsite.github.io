---
title: "Hugo相关配置记录"
subtitle: ""
date: 2023-01-14T13:08:57+08:00
draft: false
author: "小橘子Single"
authorLink: "https://hai.ergua.cc"
authorEmail: ""
description: "配置文件参数值修改"
keywords: ""
license: ""
comment: false
weight: 0

tags:
- fixIt
categories:
- hugo

hiddenFromHomePage: false
hiddenFromSearch: false

summary: ""
resources:
- name:
  src:
    
toc:
  enable: true
math:
  enable: false
lightgallery: false
seo:
  images: []

repost:
  enable: false
  url: ""

# See details front matter: https://fixit.lruihao.cn/theme-documentation-content/#front-matter
---

<!--more-->

### 主页头像设置
位置正中间
```toml
[params.home.profile]
gravatarEmail = ""  # 设置为空，否则将
avatarURL = "https://img2.baidu.com/it/u=2182807089,126304201&fm=253&fmt=auto&app=120&f=JPEG?w=200&h=200" # 设置主页头像
title = "小橘子Single"  # 首页显示标题
subtitle = "做个梦给你......"  # 首页显示字幕
```

### 主页logo设置
位置左上角
```toml
[params.header.title]
  logo = ""   # "/fixit.min.svg"  # 设置logo图片
  name = "小橘子Single"
  pre = "pre = "<i class='fab fa-grav'></i>"  # 名称之前添加额外的信息(支持HTML格式)，例如图标
  post = ""                                   # 名称之后添加额外的信息(支持HTML格式)，例如图标
```

### 浏览器图片设置
浏览器标签页
```toml
[params.app]
   svgFavicon = "https://img2.baidu.com/it/u=2182807089,126304201&fm=253&fmt=auto&app=120&f=JPEG?w=200&h=200" 
```

### 创建文章
- 默认Hugo的`archetypes`里只有`default.md`模板，copy 主题[FixIt]目录下`archetypes`里的`posts.md`模板到Hugo的`archetypes`里
```shell script
cp themes/FixIt/archetypes/posts.md  archetypes/
```
- 执行命令`hugo new posts/xxx.md` Hugo将调用`archetypes`里的`default.md`模板生成文章放在`content/posts/`目录下
```shell script
hugo new posts/test.md

Content "/your_path_hugo_blog/content/posts/test.md" created
```
- 执行命令`hugo new posts/xxx/xxx.md` Hugo将调用`archetypes`里的`posts.md`模板生成文章放在`content/posts/xxx/`目录下
```shell script
hugo new posts/test/test.md
Content "/your_path_hugo_blog/content/posts/test/test.md" created
```

### 文章模板设置
- `default.md`模板
```markdown
---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
draft: false  # 修改为false，Hugo将构建draft: false的帖子
---
```
- `posts.md`模板
```markdown
---
title: "{{ replace .TranslationBaseName "-" " " | title }}"
subtitle: ""  # 文章副标题
date: {{ .Date }}  # 创建文章时间
draft: false  # 如果为true，这篇文章将不会被构建渲染
author: "小橘子Single"  # 设置文章作者
authorLink: "http://localhost:1313/"  # 设置文章作者链接
authorEmail: ""             # 设置文章作者邮箱
description: ""             # 文章内容的描述
keywords: ""                # 文章内容的关键词
license: ""                 # 设置文章特殊的许可
comment: false              # 设置文章是否开启评论系统 (https://artalk.js.org/)
weight: 0                   # 排序，数字越小该文章排序越前

tags:                       # 设置文章标签
- draft        
categories:                 # 设置文章分类
- draft

hiddenFromHomePage: false   # 如果设为 true, 这篇文章将不会显示在主页上
hiddenFromSearch: false     # 如果设为 true, 这篇文章将不会显示在搜索结果中

summary: ""                 # 设置该文章摘要 
resources:                  # 设置本地资源引用，会在resources目录下寻找
- name: featured-image      # 图片名称
  src: featured-image.jpg   # resources目录下图片
- name: featured-image-preview
  src: featured-image-preview.jpg

toc:                        # 设置目录
  enable: true                
math:                       # 设置行内定界符
  enable: false
lightgallery: false         # 如果设为 true, 文章中的图片将可以按照画廊形式呈现
seo:                        # 页面seo配置，
  images: []                # 图片url

repost:                     # 设置为false，关闭转载            
  enable: false  
  url: ""

# See details front matter: https://fixit.lruihao.cn/theme-documentation-content/#front-matter
---

<!--more-->
```

### Emoji表情设置
- `yourblog/config.toml`
```toml
enableEmoji = true  # 开启Emoji 表情包
```

### 页脚设置
```toml
  [params.footer]
    icp = ''   # icp备案，也可以写到license里
    license = '<a rel="license external nofollow noopener noreferrer" href="https://creativecommons.org/licenses/by-nc/4.0/" target="_blank">CC BY-NC 4.0</a>| <a href="https://beian.miit.gov.cn/">桂ICP备2021001631号-1</a>'
```

### 社交信息设置
```toml
  [params.social]
    github = "yourgithub/yourgithub.github.io/"
    Email = ""
```

### GitHub Token 设置个人访问令牌
> 在 GitHub账户上，点击头像---> Settings ---> Developer settings ---> Personal access tokens ---> Generate new key ---> Tokens (classic)
>
> note描述：就是写token是干嘛。 然后选择个人令牌的访问权限，按需选择即可
>
> 我的选择范围： [repo admin:repo_hook delete_repo]
>
> 生成一个新的令牌，需要注意，新令牌的token只展示一次，需要复制下来
>
> 进入yourname.github.io仓库 ---> Settings ---> Secrets and variables ---> Action ---> New repository secret 
>
> name: 密钥名称 ACCESS_TOKEN  secret： 将刚刚复制的token粘贴到这里  添加密钥(add secret)


### GitHub Action工作流设置
- GitHub Actions 是一个持续集成和持续交付 (CI/CD) 平台，自动化构建、测试和部署管道。
- 可以创建工作流来构建和测试存储库中的每个拉取请求，或将合并的拉取请求部署到生产环境。
- [GitHub Action](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions)
- [Action](https://github.com/marketplace?type=actions)
#### 创建工作流
```shell script
mkdir -p .github/workflows/
touch .github/workflows/gh-pages.yml
```
- `gh-pages.yml`
```yaml
name: GitHub Pages   # 工作流名称，出现在GitHub存储库的"Action"选项卡中

on:                  # 要自动触发工作流，使用on定义哪些事件可以自动触发工作流运行。
  push:              # 工作流的触发器。push事件，将更改推送到存储库或合并拉​​取请求时都会触发工作流运行。
    branches:
      - main         # Set a branch to deploy 触发器会根据设置的分支去操作
  pull_request:      # 拉取分支请求
    paths:           # 事件过滤器
      - 'public/**'  
      - '.gitmodules'
      - 'themes'
      - 'config/_default/config.toml'

jobs:               # 将工作流中运行的所有作业组合在一起
  deploy:           # 作业名称
    runs-on: ubuntu-22.04   # 配置作业在22.04版本的 Ubuntu Linux 运行器上运行。作业将在 GitHub 托管的新虚拟机上执行。
    concurrency:            # 确保一次仅运行使用同一并发组的单个作业或工作流。
      group: ${{ github.workflow }}-${{ github.ref }}   # 确保同一工作流的正在进行的运行
    steps:         # 将作业中运行的所有步骤组合在一起。类似于一个工作流程
      - uses: actions/checkout@v3    # 将存储库签出到运行器上的操作 
        with:
          submodules: true  # Fetch Hugo themes (true OR recursive) # 获取Hugo主题
          fetch-depth: 0    # Fetch all history for .GitInfo and .Lastmod 

      - name: Setup Hugo    # 在steps下，类似步骤 1 安装Hugo
        uses: peaceiris/actions-hugo@v2  # 此步骤使用操作安装指定版本的Hugo
        with:
          hugo-version: '0.91.2' # 根据你自己的本地Hugo版本填写
          extended: true         # 设置扩展Hugo
 
      - name: Build        # 在steps下，类似步骤 2 构建Hugo
        run: hugo --minify

      - name: Deploy       # 在steps下，类似步骤 3 部署pages
        uses: peaceiris/actions-gh-pages@v3              # 部署到gh-pages分支
        if: ${{ github.ref == 'refs/heads/main' }}       # 使用并发操作部署
        with:
          github_token: ${{ secrets.ACCESS_TOKEN }}      # 个人访问令牌填到这里
          publish_dir: public
          cname: your domain   # 自定义域名
```

### 推送GitHub
- 将本地Hugo项目推送至GitHub，会自动触发Action构建部署pages
```shell script
git add .                  
git commit -m "notes"
git remote add origin git@github.com:yourname/yourname.github.io.git
git pull
git push -u origin main
```

