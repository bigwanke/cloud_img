title: 在gitee上使用pages服务搭建Hexo博客

#### 1. 安装node.js

因为Hexo是基于nodejs的，所以要使用Hexo，那么第一步肯定是安装nodejs。安装分为以下几个步骤：

1. 下载[node.js](https://links.jianshu.com/go?to=https%3A%2F%2Fnodejs.org%2F)

2. 安装node.js,安装完成之后可以在终端输入`node -v`和`npm -v`查看是否安装成功，这两条命令如果都输出了版本号，那么就表示安装成功了。

   ```shell
   npm config set registry https://registry.npm.taobao.org
   ```

#### 2.安装Git

1. 下载[Git](https://links.jianshu.com/go?to=https%3A%2F%2Fgit-scm.com%2F)
2. 安装，可以通过`git --version`命令检查是否安装成功，如果输出了版本号，则安装成功

#### 3.安装Hexo

1. 执行安装命令

   ```shell
   npm install hexo-cli -g
   ```

2. 执行`hexo -v`,若是出现版本信息则安装成功

#### 4.创建Hexo博客（个人网站）文件夹

Hexo已经安装完成，现在我们要做的就是使用Hexo来初始化一个我们存放博客或者说是个人网站资源的文件夹。

进入你需要安装的位置目录，执行命令：

```shell
hexo init blog                     //blog是创建的目录，可以自定义
```

进入你选择的安装目录，可以看到已经生成了一个blog文件夹，通过命令提示符进入blog目录,执行命令用于更新nodejs的模块：

```shell
npm install
```

完成后在该目录下执行如下命令：

```shell
hexo server
```

输出如下：

```shell
INFO  Validating config
INFO  Start processing
INFO  Hexo is running at http://localhost:4000 . Press Ctrl+C to stop.
```

说明你的hexo服务已经启动了，浏览器输入链接即可访问你的个人博客主页

![image-20210926221943893](C:\Users\wanke\AppData\Roaming\Typora\typora-user-images\image-20210926221943893.png)

虽然已经看到了页面，但是所有的配置都是默认的，我们还需要做一些修改。在该文件夹下面，找到`_config.yml`文件，这个文件是Hexo的配置文件，大体如下：

```yaml
# Hexo Configuration
## Docs: https://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site
title: 你的博客(个人网站)名称
subtitle: 你的博客(个人网站)子名称
description: '你的博客（个人网站）的描述'
keywords: 你的博客（个人网站）的关键字
author: 你的博客（个人网站）的作者
language: 你的博客（个人网站）语言 en：英文 zh-CN：简体中文
timezone: '时区（可以不用配置）'

# URL
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: 你的博客（个人网站）网址
root: /
permalink: :year/:month/:day/:title/
permalink_defaults:
pretty_urls:
  trailing_index: true # Set to false to remove trailing 'index.html' from permalinks
  trailing_html: true # Set to false to remove trailing '.html' from permalinks

# Directory
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:

# Writing
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link:
  enable: true # Open external links in new tab
  field: site # Apply to the whole site
  exclude: ''
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  auto_detect: false
  tab_replace: ''
  wrap: true
  hljs: false

# Home page setting
# path: Root path for your blogs index page. (default = '')
# per_page: Posts displayed per page. (0 = disable pagination)
# order_by: Posts order. (Order by date descending by default)
index_generator:
  path: ''
  per_page: 10
  order_by: -date

# Category & Tag
default_category: uncategorized
category_map:
tag_map:

# Metadata elements
## https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meta
meta_generator: true

# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss
## Use post's date for updated date unless set in front-matter
use_date_for_updated: false

# Pagination
## Set per_page to 0 to disable pagination
per_page: 10
pagination_dir: page

# Include / Exclude file(s)
## include:/exclude: options only apply to the 'source/' folder
include:
exclude:
ignore:

# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: landscape

# Deployment
## Docs: https://hexo.io/docs/deployment.html
deploy:
  type: ''
```

配置一下你博客的个人信息，其余可以默认

#### 5.注册Gitee账号

既然是通过Gitee搭建博客，那肯定是需要Gitee账号的，[点击注册Gitee](https://links.jianshu.com/go?to=https%3A%2F%2Fgitee.com)。

#### 6.创建Gitee仓库

注册好Gitee账号就可以创建一个仓库了，点击头像旁边的+，然后点击创建仓库

![image-20210926222747955](C:\Users\wanke\AppData\Roaming\Typora\typora-user-images\image-20210926222747955.png)

![image-20210926224602600](C:\Users\wanke\AppData\Roaming\Typora\typora-user-images\image-20210926224602600.png)

填入相应信息，点击创建

#### 7.提交文件到Gitee仓库前的准备工作

将本地文件推送到Gitee仓库之前，我们需要做一些简单的配置。

在终端输入命令配置Git提交时的用户名和邮箱：

```shell
git config --global user.name "username" //全局配置提交是使用的提交人名
git config --global user.email "xxx@mail.com" //全局配置提交人的电子邮箱
```

如果想每次提交的时候不输入用户名和密码就需要在本地生成ssh秘钥。

在终端输入：

```shell
ssh-keygen -t rsa -C "公钥描述"
```

生成的秘钥会存放在`~/.ssh/`目录下。

接下来在终端输入：

```shell
cat ~/.ssh/id_rsa.pub
```

就可以看到生成的公钥内容了，将公钥的内容复制下来放到Gitee上。

进入到你的Gitee主页，点击"设置"，点击SSH公钥，然后添加

![image-20210926225003158](C:\Users\wanke\AppData\Roaming\Typora\typora-user-images\image-20210926225003158.png)

#### 8.上传blog

本地博客（个人网站）目录已经生成，Gitee仓库已经创建，现在我们需要将本地的文件推送到Gitee仓库了。

因为GiteePages是支持Hexo资源编译的，所以需要推送到Gitee仓库的文件就有两种选择。

只推送Hexo生成的静态文件到Gitee仓库

第一种：

这种方式是直接将Hexo生成的所有静态文件推送到Gitee仓库，这样就相当于是GiteePages托管的就是你的博客（个人网站的）所有生成好的静态文件，就不需要GiteePages再去编译生成一次静态文件。这样每次更新GiteePages的时候时间会相对短一些。这种方式还有个好处就是操作简单一点，可直接通过Hexo命令来推送文件到Gitee仓库。

使用终端，进入到博客（个人网站）文件夹下面，执行命令安装一个插件：

```shell
npm i hexo-deployer-git
```

装好插件之后，在该目录下找到`_config.yml`文件，打开文件配置你的仓库信息：

```yaml
#在文件中找到这个deploy这个节点，修改或添加配置deploy:  type: git  repo: 你的仓库地址  branch: 你要推送到仓库的分支（默认为master）
```

在该目录下执行：

```shell
hexo g
```

这个命令会根据你的Markdown文件生成对应的静态文件，生成好了之后，可本地启动Hexo服务看下效果，输入命令：

```shelll
hexo s //和hexo server命令一样
```

感觉效果满意了，就可以提交到Gitee仓库了，执行命令：

```shell
hexo d
```

至此，生成的静态文件就已经推送到Gitee仓库去了。

第二种：

这种方式是将你初始化的博客（个人网站）整个文件夹下面的所有文件推送到Gitee仓库，GiteePages在更新的时候会自动的去编译一次你的目录，然后生成所有的的静态文件，这样的话，每次更新GiteePages的时候肯定时间就相对会久一点。

在终端进入到之前初始化的博客（个人网站）文件夹中，执行命令：



```shell
git init //将该文件夹中的文件纳入到Git的版本控制中git add . //将所有的文件添加到Git暂存区git commit -m "此次提交的说明" //将文件提交到本地git remote add origin 你的远程仓库地址 //告诉Git你的Gitee仓库在哪里git push -u origin master //将你本地的文件提交到Gitee仓库的master分支
```

至此，你的博客（个人网站）的所有文件已经提交到了Gitee仓库去了。

ps：Gitee仓库地址需要进入你创建的仓库首页才能看到，既然配置了公钥，那么仓库地址肯定是使用ssh协议最好。

![img](https:////upload-images.jianshu.io/upload_images/2978725-01900f651983b4cb?imageMogr2/auto-orient/strip|imageView2/2/w/1200/format/webp)

现在是万事具备，只欠开启GiteePages服务了。

#### 9.开启pages服务

现在进入到你的Gitee仓库页面，找到`服务`，点击`Gitee Pages`开启GiteePages服务

![image-20210926230331393](C:\Users\wanke\AppData\Roaming\Typora\typora-user-images\image-20210926230331393.png)

如果这是你第一次使用pages服务，应该会需要实名制，根据gitee官方给的提示操作即可，一般会在一个工作周内完成审核，完成审核后

![image-20210926230422563](C:\Users\wanke\AppData\Roaming\Typora\typora-user-images\image-20210926230422563.png)

勾选强制使用HTTPS，点击启动，可以看到提示Gitee Pages服务已启动，并给了一个网址。

现在可以直接通过这个网址访问你的博客了

![image-20210926230611252](C:\Users\wanke\AppData\Roaming\Typora\typora-user-images\image-20210926230611252.png)

访问网址，如果出现获取不到样式的问题（如下图）：

![image-20210926231302754](C:\Users\wanke\AppData\Roaming\Typora\typora-user-images\image-20210926231302754.png)

是因为部署的仓库和自己的个性地址不一致导致的，解决方案请看[请看官方指导](https://gitee.com/help/articles/4136#article-header0)。

#### 10.下载主题

hexo默认的主题不是很好看，可以进入Gitee搜索hexo-theme，可以找到很多好看的主题，选择你喜欢的主题根据主题的README.md文件进行操作。

这里以下载hexo-theme-butterfly为例

进入博客根目录，执行命令

```shell
npm i hexo-theme-butterfly
```

修改配置文件_config.yml,把主题改为Butterfly

```yaml
theme: butterfly
```

如果你没有pug以及stylus的渲染器，請下载安裝： 

```shell
npm install hexo-renderer-pug hexo-renderer-stylus --save
```

提交文件

```shell
hexo ghexo d
```

然后进入Gitee,进入你的仓库，点击Gitee pages服务，点击更新，重新部署。

![image-20210927110302869](C:\Users\wanke\AppData\Roaming\Typora\typora-user-images\image-20210927110302869.png)

