# docs

记住，说的再多不如动手上手测验，如果你想熟练使用Git工具，那么你可以试试Hexo博客，搭建一个自己的网站，在搭建过程中你将了解到markdown和git的基本使用方法，同时，你也可以在网站上分享自己的一些自己的心得体会。



## Git使用

Git 是一个开源的分布式版本控制系统，用于敏捷高效地处理任何或小或大的项目。

Git 是 Linus Torvalds 为了帮助管理 Linux 内核开发而开发的一个开放源码的版本控制软件。

Git 与常用的版本控制工具 CVS, Subversion 等不同，它采用了分布式版本库的方式，不必服务器端软件支持。



对于编程来说，Git有着很多作用，最重要的就是版本管理，让你知道每次提交的代码内容和修改内容，同时团队开发也利于协同工作，在真实工作中，Git是重要的组成部分。

不过，在本科教育中，似乎大多数学校不会教授关于Git的使用方法，最多提一句，因此自学使用Git管理工具是非常重要的。

![img](https://www.runoob.com/wp-content/uploads/2015/02/git-process.png)

具体使用可以参考[Git 教程 | 菜鸟教程 (runoob.com)](https://www.runoob.com/git/git-tutorial.html)，本文主要讲授理论知识，说得再多不如自己动手操作实现。

如果你还是不清楚，可以参考B站相关视频

同时，你需要确保你能够与远程Git仓库相连接，境内互联网对于Github不够友好，因此你需要通过某些方式使用Github作为远程仓库，在此不进行赘述，或者你可以使用国内的替代平台，例如coding,码云等。



## Git 五分钟教程

### *分类* [编程技术](https://www.runoob.com/w3cnote_genre/code)

许多人认为 Git 太混乱，或认为它是一种复杂的版本控制系统，其实不然，这篇文章有助于大家快速上手使用 Git。

![img](https://www.runoob.com/wp-content/uploads/2015/02/git.jpg)

## 入门

使用Git前，需要先建立一个仓库(repository)。您可以使用一个已经存在的目录作为Git仓库或创建一个空目录。

使用您当前目录作为Git仓库，我们只需使它初始化。

```
git init
```

使用我们指定目录作为Git仓库。

```
git init newrepo
```

从现在开始，我们将假设您在Git仓库根目录下，除非另有说明。

### 添加新文件

我们有一个仓库，但什么也没有，可以使用add命令添加文件。

```
git add filename
```

可以使用add... 继续添加任务文件。

### 提交版本

现在我们已经添加了这些文件，我们希望它们能够真正被保存在Git仓库。

为此，我们将它们提交到仓库。

```
git commit -m "Adding files"
```

如果您不使用-m，会出现编辑器来让你写自己的注释信息。

当我们修改了很多文件，而不想每一个都add，想commit自动来提交本地修改，我们可以使用-a标识。

```
git commit -a -m "Changed some files"
```

git commit 命令的-a选项可将所有**被修改或者已删除的且已经被git管理的文档**提交到仓库中。

千万注意，-a不会造成新文件被提交，只能修改。

### 发布版本

我们先从服务器克隆一个库并上传。

```
git clone ssh://example.com/~/www/project.git
```

现在我们修改之后可以进行推送到服务器。

```
git push ssh://example.com/~/www/project.git
```

### 取回更新

如果您已经按上面的进行push，下面命令表示，当前分支自动与唯一一个追踪分支进行合并。

```
git pull
```

从非默认位置更新到指定的url。

```
git pull http://git.example.com/project.git
```

## 已经超过了五分钟？

### 删除

如何你想从资源库中删除文件，我们使用rm。

```
git rm file
```

### 分支与合并

分支在本地完成，速度快。要创建一个新的分支，我们使用branch命令。

```
git branch test
```

branch命令不会将我们带入分支，只是创建一个新分支。所以我们使用checkout命令来更改分支。

```
git checkout test
```

第一个分支，或主分支，被称为"master"。

```
git checkout master
```

对其他分支的更改不会反映在主分支上。如果想将更改提交到主分支，则需切换回master分支，然后使用合并。

```
git checkout master
git merge test
```

如果您想删除分支，我们使用-d标识。

```
git branch -d test
```

## 相关文章

- Github 简明教程：[http://www.runoob.com/w3cnote/git-guide.html](https://www.runoob.com/w3cnote/git-guide.html)
- Git 教程：[http://www.runoob.com/git/git-tutorial.html](https://www.runoob.com/git/git-tutorial.html)

> 来源：http://itmyhome.com/2015/01/git-five-minutes-tutorial



### Git commit规范

在学习完Git之后你已经初步学会使用Git工具了，如果你已经使用git进行过了相关操作，并且添加好了你的远程仓库，那么当你修改后你得代码之后需要进行git commit操作，同时也需要携带信息，用于表明此次代码提交信息，方便自己和团队查看。

### **Header**

Header 部分只有一行，包括三个字段：`type`（必需）、`scope`（可选）和`subject`（必需）。

- `type`: 用于说明 commit 的类型。一般有以下几种:
  feat: 新增feature
  fix: 修复bug
  docs: 仅仅修改了文档，如readme.md
  style: 仅仅是对格式进行修改，如逗号、缩进、空格等。不改变代码逻辑。
  refactor: 代码重构，没有新增功能或修复bug
  perf: 优化相关，如提升性能、用户体验等。
  test: 测试用例，包括单元测试、集成测试。
  chore: 改变构建流程、或者增加依赖库、工具等。
  revert: 版本回滚
- `scope`: 用于说明 commit 影响的范围，比如: views, component, utils, test...
- `subject`: commit 目的的简短描述

### **Body**

对本次 commit 修改内容的具体描述, 可以分为多行。如下图:

```text
# body: 72-character wrapped. This should answer:
# * Why was this change necessary?
# * How does it address the problem?
# * Are there any side effects?
# initial commit
```

### **Footer**

一些备注, 通常是 `BREAKING CHANGE`(当前代码与上一个版本不兼容) 或修复的 bug(关闭 Issue) 的链接。

简单介绍完上面的规范，我们下面来说一下`commit.template`，也就是 git 提交信息模板。



通常情况下你可以只修改Header部分即可，更多规范你可以查看这些优秀项目：

[twikoojs/twikoo: 💬 一个简洁、安全、免费的静态网站评论系统 | A simple, safe, free comment system. (github.com)](https://github.com/twikoojs/twikoo/commits/main)

[redis/go-redis: Redis Go client (github.com)](https://github.com/redis/go-redis/commits/master)

以及我这个前期没有规范的垃圾项目：

[Commits · Tianli-CDN/cdn-server (github.com)](https://github.com/Tianli-CDN/cdn-server/commits/main)



### Git branch管理

git branch即分支，就像这样。中间蓝色的可视为主要开发线 `main/master`，而其他的视为支线分支防止与主要开发线冲突，也可以防止项目大变动导致的主要开发线不可用。 

![](https://static.runoob.com/images/svg/git-brance.svg)

当我们使用Git进行版本控制时，分支是一个非常强大的功能。以下是有关Git分支的一些重要信息：

1. 分支的作用：
   - 允许我们在同一项目中同时进行不同的工作，并且可以在工作完成后将其合并到主分支中。
   - 允许多个开发人员在同一代码库中并行开发，而不干扰彼此的工作。
   - 提供了一种轻量级的方法来尝试新功能或修复问题，而不影响主分支。
2. 常用Git分支命令：
   - 创建新分支：`git branch <branch-name>`
   - 切换分支：`git checkout <branch-name>`
   - 创建并切换到新分支：`git checkout -b <branch-name>`
   - 查看所有分支：`git branch`
   - 合并分支：`git merge <branch-name>`
   - 删除分支：`git branch -d <branch-name>`
   - 强制删除分支：`git branch -D <branch-name>`
3. Git分支的工作流程：
   - 创建一个新分支以开展独立的工作。
   - 切换到该分支并对代码进行修改、添加新功能或修复问题。
   - 提交更改并在需要时推送到远程仓库。
   - 如果工作完成，将分支合并到主分支（通常是master或main）。
   - 执行测试以确保合并没有引入新的问题。
   - 删除不再需要的分支。

### Git tags管理

1. 标签的作用：
   - 标记版本：标签可以用来标记项目的重要版本，以便稍后可以方便地访问和回顾每个版本的代码。
   - 发布软件：使用标签来标记软件的正式发布版本，方便用户和开发者识别和访问。
   - 标记里程碑：可以使用标签来表示项目中重要的里程碑或关键事件。
2. 常用Git标签命令：
   - 创建轻量标签：`git tag <tag-name>`
   - 创建带注释的标签：`git tag -a <tag-name> -m "tag-message"`
   - 查看所有标签：`git tag`
   - 查看特定标签的详细信息：`git show <tag-name>`
   - 将标签推送到远程仓库：`git push origin <tag-name>`
   - 将所有标签推送到远程仓库：`git push origin --tags`
   - 删除本地标签：`git tag -d <tag-name>`
   - 删除远程标签：`git push origin --delete <tag-name>`
3. Git标签的类型：
   - 轻量标签（Lightweight Tags）：简单的指向特定提交的引用，没有附加的元数据。
   - 带注释的标签（Annotated Tags）：包含附加的元数据，如标签的创建者、创建时间、注释等。
4. 示例：比如你今天完成了一个重要项目的开发。要发布一个软件的版本号，那么你可以使用Git工具给当前代码打个版本号标签，然后发布release。

## Git链接远程仓库（建议动手）

建议参考[Git 远程仓库(Github) | 菜鸟教程 (runoob.com)](https://www.runoob.com/git/git-remote-repo.html)

## Github使用（仅提示部分内容，建议动手）

注：此内容需要一些手段连接github，否则无法进入网站

GitHub 是一个面向开源及私有软件项目的托管平台，因为只支持 Git 作为唯一的版本库格式进行托管，故名 GitHub。

GitHub 于 2008 年 4 月 10 日正式上线，除了 Git 代码仓库托管及基本的 Web 管理界面以外，还提供了订阅、讨论组、文本渲染、在线文件编辑器、协作图谱（报表）、代码片段分享（Gist）等功能。目前，其托管版本数量非常之多，而且其中不乏知名开源项目，例如 Ruby on Rails、jQuery、python 等。

作为开源代码库以及版本控制系统，Github 拥有超过千万的开发者用户。随着越来越多的应用程序转移到了云上，Github 已经成为了管理软件开发以及发现已有代码的首选方法。

如前所述，作为一个分布式的版本控制系统，在 Git 中并不存在主库这样的概念，每一份复制出的库都可以独立使用，任何两个库之间的不一致之处都可以进行合并。

GitHub 可以托管各种 Git 库，并提供一个 web 界面，但与其它像 SourceForge 或 Google Code 这样的服务不同，GitHub 的独特卖点在于从另外一个项目进行分支的简易性。为一个项目贡献代码非常简单：首先点击项目站点的Fork的按钮，然后将代码检出并将修改加入到刚才分出的代码库中，最后通过内建的pull request机制向项目负责人申请代码合并。

Github是目前开源项目的核心平台，比如你使用的安卓系统，各种chromium应用都是基于此托管平台的项目而来的。

今天，GitHub已是：

- 一个拥有143万开发者的社区。其中不乏Linux发明者[Torvalds](https://github.com/torvalds)这样的顶级黑客，以及Rails创始人[DHH](https://github.com/dhh)这样的年轻极客。
- 这个星球上最流行的开源托管服务。目前已托管431万git项目，不仅越来越多知名开源项目迁入GitHub，比如Ruby on Rails、jQuery、Ruby、Erlang/OTP；近三年流行的开源库往往在GitHub首发，例如：[BootStrap](https://github.com/twitter/bootstrap)、[Node.js](https://github.com/joyent/node)、[CoffeScript](https://github.com/jashkenas/coffee-script)等。
- alexa全球排名414的网站。



不过，在了解这个平台之前你需要首先了解项目内的开源协议License

### 开源协议介绍

![img](https://www.runoob.com/wp-content/uploads/2018/03/da68b98e404578126b87c5afd9ba9bc3.png)

![img](https://www.runoob.com/wp-content/uploads/2018/03/bg2011050101.png)

在git托管平台除特殊声明外一般情况下都有License这个文件，同时托管平台也会标识出具体的协议，你需要严格遵守协议内容，这对于一个开发者来说是非常重要的。如果某些协议导致你不能闭源，那么你可以写一个中间件为你的项目闭源，防止版权问题，你自己开源也要根据你的需求自行添加协议说明。

### 进阶介绍

最基础的东西不需要过多介绍，建议还是自己上手用一用，动动手，注册一个账号然后登录就像，网站虽然是英文，但是大多数东西还是能看懂啥意思，即使看不懂，可以使用浏览器插件进行翻译。

Github为大家提供了很多工具，比如Github Actions，当你写好这个之后，你可以通过github action帮你完成项目编译，代码格式化，等等自动化任务，对于很多开发者来说这是非常好的，毕竟当你完成某项代码的开发之后，你可能没有你需要运行的环境的对应系统，而且某些语言也没交叉编译链，或者是你看见有一个小BUG，直接通过github在手机上就把他改掉了。这个时候Github Actions就显得非常重要了。比如，我的一个项目[SZCU-SNC/Autologin_win: 校园网自动登录的windows服务端 (github.com)](https://github.com/SZCU-SNC/Autologin_win)

在`/.github/workflows/go_deploy.yml`目录下有以下内容

```yaml
name: Go Release Action

on:
  push:
    tags:
      - '*'

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout repository
      uses: actions/checkout@v3
      
    - name: Setup Go environment
      uses: actions/setup-go@v3
      with:
        go-version: 1.19

    - name: Build binaries
      run: |
        GOOS=windows GOARCH=amd64 go build -ldflags "-s -w -H=windowsgui" -o Autologin.exe -v


    - name: Create Release
      id: create_release
      uses: actions/create-release@v1
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      with:
        tag_name: ${{ github.ref }}
        release_name: Release ${{ github.ref }}
        body: Action自动打包
        draft: false
        prerelease: false



    - name: Upload Windows Binary
      uses: actions/upload-release-asset@v1
      env:
        GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
      with:
        upload_url: ${{ steps.create_release.outputs.upload_url }}
        asset_path: ./Autologin.exe
        asset_name: Autologin.exe
        asset_content_type: application/octet-stream
```

以上是yaml

YAML 是 "YAML Ain't a Markup Language"（YAML 不是一种标记语言）的递归缩写。在开发的这种语言时，YAML 的意思其实是："Yet Another Markup Language"（仍是一种标记语言）。

YAML 的语法和其他高级语言类似，并且可以简单表达清单、散列表，标量等数据形态。它使用空白符号缩进和大量依赖外观的特色，特别适合用来表达或编辑数据结构、各种配置文件、倾印调试内容、文件大纲（例如：许多电子邮件标题格式和YAML非常接近）。

YAML 的配置文件后缀为 **.yml**，如：**runoob.yml** 。

主要用来写配置文件。不需要单独专门学习，有需要的话去搜索一下语法就好了。

言归正传，主要介绍action配置。可以看见以上示例中非常简单易懂，以上配置能够完成当我上传git tag时，action会自动触发，并且构建Windows环境可使用的二进制文件再发布release。

具体了解就需要参考文档了。幸运的是，github为我们提供了中文文档。

[GitHub Actions 文档 - GitHub 文档](https://docs.github.com/zh/actions)

（注意，action某些权限需要你单独配置，了解这个我还是建议先动手搭建个hexo博客练手）

## markdown

Markdown 是一种轻量级标记语言，它允许人们使用易读易写的纯文本格式编写文档。

Markdown 语言在 2004 由约翰·格鲁伯（英语：John Gruber）创建。

Markdown 编写的文档可以导出 HTML 、Word、图像、PDF、Epub 等多种格式的文档。

Markdown 编写的文档后缀为 **.md**, **.markdown**。

如果你细心观察就会发现，几乎每一个仓库都有readme.md，这是仓库的说明文档，你可以在此编写内容。

1. 专注于文字内容；
2. 纯文本，易读易写，可以方便地纳入版本控制；
3. 语法简单，没有什么学习成本，能轻松在码字的同时做出美观大方的排版。

![The Markdown Process](data:image/png;base64,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)

​	[Markdown 官方教程](https://markdown.com.cn/)  在此你可以学习到基础语法，如果你不喜欢这种方式，也可以使用富文本编辑器，最出名的莫过于[Typora — a markdown editor, markdown reader.](https://typora.io/?ref=appmakes)在富文本编辑器里面，你可以使用更符合直觉的方法写出文字。就像word一样，但是比word更简单。



## json

JSON（全称JavaScript Object Notation，中文为JavaScript对象表示法）是一种轻量级的数据交换格式。它以简洁、清晰的格式表示结构化数据，非常适合用于Web应用之间的数据传输。JSON被广泛应用于前后端数据传递、配置文件、数据存储等场景。

JSON的语法规则相对简单，使用键值对表示数据，并使用大括号（{}）包围对象，使用方括号（[]）包围数组。键和值之间使用冒号（:）分隔，键值对之间使用逗号（,）分隔。以下是一个简单的JSON示例：

```
{
  "name": "John",
  "age": 30,
  "city": "New York"
}
```

在代码中使用JSON时，可以使用现代编程语言的内置函数或库来解析和生成JSON数据。以下是一些常见编程语言的JSON处理文档和链接：

- JSON在JavaScript中的处理：[JSON对象文档](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/JSON)（Mozilla开发者网络）
- JSON在Python中的处理：[json模块文档](https://docs.python.org/zh-cn/3/library/json.html)（Python官方文档）
- JSON在Java中的处理：[Jackson库](https://github.com/FasterXML/jackson)、[Gson库](https://github.com/google/gson)
- JSON在C#中的处理：[Json.NET库](https://www.newtonsoft.com/json)
- JSON在Ruby中的处理：[JSON文档](https://ruby-doc.org/stdlib-2.7.3/libdoc/json/rdoc/JSON.html)（Ruby官方文档）
- .......

这仅是一些常见编程语言的JSON处理链接

json可以用来做以下事情

1. 数据交换：JSON常用于Web应用程序和服务器之间的数据交换。它可以轻松地将数据从服务器发送到客户端，并将客户端发送的数据传递给服务器。
2. 存储配置文件：JSON可以用来存储和读取应用程序的配置文件。通过将配置信息保存为JSON格式，可以方便地修改和读取这些配置。
3. Web服务数据传输：许多Web服务使用JSON作为数据传输格式。例如，许多开放的API（Application Programming Interface）使用JSON来发送和接收数据。
4. 统一数据格式：JSON提供了一种统一的数据格式，使不同应用程序和平台之间可以更轻松地交换数据。
5. NoSQL数据库：一些NoSQL数据库（如MongoDB）使用JSON格式来存储和查询数据。这使得存储和检索数据更加灵活和易于使用。

现在不妨打开任意一个网站，打开F12分析网络请求，细心寻找你会发现，似乎所有信息传输都是通过JSON的。毫无疑问，json也是极其重要的。

[JSON 教程 | 菜鸟教程 (runoob.com)](https://www.runoob.com/json/json-tutorial.html)
