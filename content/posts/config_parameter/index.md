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
- FixIt
categories:
- Hugo

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

## 配置文件参数值修改
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
  typeit = true    # 打字机效果
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

### 添加友链
#### 创建友链模板
- 在根目录下创建一个友链模板 
- `layouts/friends/single.html`
```html
{{- define "title" }}{{ .Title }} - {{ .Site.Title }}{{ end -}}

{{- define "content" -}}
    {{- $params := .Scratch.Get "params" -}}
    <div class="page single special">
        {{- /* Title */ -}}
        <h1 class="single-title animated pulse faster">
            {{- .Title -}}
        </h1>

        {{- /* Subtitle */ -}}
        {{- with $params.subtitle -}}
            <h2 class="single-subtitle">{{ . }}</h2>
        {{- end -}}

        {{- /* Friend links */ -}}
        {{- $loading := resources.Get "svg/loading.svg" | minify -}}
        <script src="//at.alicdn.com/t/font_578712_g26jo2kbzd5qm2t9.js"></script>
        <link rel="stylesheet" href="/friends/css/_friends.css" />
        <div class="friend-links">
            {{ range $index, $friend := .Site.Data.friends }}
                <a
                    class="friend-link"
                    title="{{ $friend.description }}"
                    href="{{ $friend.url | safeURL }}"
                    rel="external nofollow noopener noreferrer"
                    target="_blank">
                    {{ if $friend.avatar }}
                        <img
                            class="friend-avatar lazyload" 
                            src="{{ $loading.RelPermalink }}"
                            data-src="{{ $friend.avatar }}"
                            alt="{{ $friend.nickname }}" />
                    {{ else }}
                        <svg class="friend-avatar" aria-hidden="true">
                            <use xlink:href="#icon-{{ add 1 $index }}"></use>
                        </svg>
                    {{ end }}
                    <span class="friend-nickname" title="{{ $friend.nickname }}">@{{ $friend.nickname }}</span>
                </a>
            {{ end }}
        </div>

        {{- /* Content */ -}}
        <div class="content" id="content">
            {{- dict "Content" .Content "Ruby" $params.ruby "Fraction" $params.fraction "Fontawesome" $params.fontawesome | partial "function/content.html" | safeHTML -}}
        </div>

        {{- /* Comment */ -}}
        {{- partial "comment.html" . -}}
    </div>
{{- end -}}
```
- 或者 cp 主题下的友链模板
```shell script
cp themes/FixIt/layouts/friends/   layouts/friends/
```

#### 友链模板样式
- 新建`_friends.css`文件
```css
/**
 * @Description: Style of layout named 'Friend links'.
 * @Author: lruihao.cn
 * @Updated:  2021/9/20 19:26
 */
 
.friend-links {
  margin-top: 1rem;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  flex-wrap: wrap;
}
@media (max-width: 576px) {
  .friend-links {
    justify-content: space-around;
  }
}
.friend-link {
  width: 150px;
  height: 200px;
  font-size: 1rem;
  text-align: center;
  background: rgba(255,255,255,0.3);
  box-sizing: border-box; 
  box-shadow: 3px 3px 5px #aaa;
  border-radius: 5px;
  border:none;
  transition-duration: 0.3s;
  margin-bottom: 1rem;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.friend-link:hover {
  background: #fff;
  transform: scale(1.03);
  box-shadow: 0 0 3px #aaa;
}
.friend-avatar {
  object-fit: cover;
  object-position: center;
  width: 100%!important;
  height: 150px!important;
  border-radius: 5px;
  margin: 0;
  padding: 0;
}
.friend-nickname{
  display: block;
  position: relative;
  color: #2bbc8a;
  font-weight: bold;
  max-width: 100%;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  line-height: 18px;
  margin-bottom: 1rem;
}
.friend-nickname:hover {
  color: #d480aa;
}
```
#### 友链页面设置
- 新建`friends/index.md`
```shell script
hugo new friends/index.md
```
1、将`_friends.css`文件放到 `content/friends/css/`目录下
```shell script
mkdir content/friends/css
mv _friends.css content/friends/css/
```

2、打开友链页面 `content/friends/index.md`
```markdown
---
title: "友情链接"
subtitle: "需要交换友链下方留言哦 ~"
type: "friends"
date: 2023-02-03T09:31:19+08:00
description: "小橘子Single' blog"
keywords: 
  - Hugo
  - friends template
comment: false
---
<!-- When you set data `friends.yml` in `yourProject/data/` directory, it will be automatically loaded here. -->
---
<!-- You can define additional content below for this page. -->
```

#### 添加友链
- 新建数据文件 `data/friends.yml`
```yaml
# - nickname: 标题
#   avatar: 头像
#   url: 站点
#   description: 描述

- nickname: Lruihao
  avatar: https://lruihao.cn/images/avatar.jpg
  url: https://lruihao.cn
  description: 不怕萬人阻擋，只怕自己投降
```

#### 配置添加友链
- config.toml
```yaml
  [[menu.main]]
    identifier = "friends"
    pre = ""
    post = ""
    name = "友链"
    url = "/friends/"
    title = ""
    weight = 3
    [menu.main.params]
      icon = "fa-solid fa-users"
```

### 评论系统设置
- [Utterances 文档](https://utteranc.es)
- [utterances 安装链接](https://github.com/apps/utterances) 评论系统设置

1.安装utterances
> 打开 utterances 安装链接 ---> 右上角安装 ---> 选择 Only select repositories ---> 点击install

2.在根目录下修改`config.toml`配置文件，开启评论
```toml
      [params.page.comment.utterances]
        enable = false
        # owner/repo
        repo = "liangsite/utterances"
        issueTerm = "title"   # 这个参数可选pathname、url、title 
        label = ""
        lightTheme = "github-light"
        darkTheme = "github-dark"
```

{{< admonition tip "提示" false >}}
文章开头将`comment: falase` 这个参数删除，否则页面将不会显示评论。
{{< /admonition >}}

### 推送GitHub
- 将本地Hugo项目推送至GitHub，会自动触发Action构建部署pages
```shell script
git add .                  
git commit -m "notes"
git remote add origin git@github.com:yourname/yourname.github.io.git
git pull
git push -u origin main
```

