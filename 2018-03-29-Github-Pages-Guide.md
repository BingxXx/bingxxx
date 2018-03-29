---
title: GitHub Pages 指南
layout: post
---

#  GitHub Pages 指南
GitHub Pages 可以为你或者你的项目提供介绍网页，它是由 GitHub 官方托管和发布的。你可以使用 GitHub 提供的页面自动生成器，GitHub App 或者命令行来创建 GitHub Pages。

本指南是 GitHub Pages 官网 [GitHub Pages Basics](https://help.github.com/categories/github-pages-basics/) 的中文翻译版本。

适用人群
本教程是给那些想详细了解如何使用 GitHub Pages 的开发人员编写的。

学习前提
在学习本教程之前，你需要对 Git 操作和网站前端相关的知识有一定了解。

你将学会
* GitHub Pages 的在线创建或手动创建
* GitHub Pages 中使用 Jekyll
* GitHub Pages 中使用自定义域名

|更新日期|更新内容|
|---|---|
|2015-07-14|GitHub Pages 指南|

## GitHub Pages 是什么
GitHub Pages 是通过我们网站托管和发布的公开网页。

你可以通过 [Automatic Page Generator](https://help.github.com/articles/creating-pages-with-the-automatic-generator) 在线创建和发布 GitHub Pages。如果你更喜欢本地操作，你可以使用 Mac 或者 Windows 平台的 GitHub App，或者使用 命令行。

Pages 是通过 HTTP 服务的，不是 HTTPS，所以你不应该使用它处理敏感的事务，像发送密码或者信用卡号码。

警告：GitHub Pages 网站是在互联网上公开的，即使它们所在的库是私有的。如果你有敏感的数据在 Page 库，你应该在发布之前删除它。

想要获取更多信息，可以查看 [Github Pages](http://pages.github.com/) 网页，或者这里的 [相关帮助文档](https://help.github.com/categories/github-pages-basics/)。

## 用户、组织和项目 Pages
这里有两种基本的 GitHub Pages 类型：用户/组织 Pages 和项目 Pages。它们极其相似，但是有一些很重要的差别。

两种类型的 Pages 都是使用 HTTP 服务，不是 HTTPS。你不应该使用它处理敏感信息，像发送密码或者信用卡号码。

请注意 Pages 发布之后都是公开的，即使它所在的库是私有的。

### 用户/组织 Pages
用户/组织 Pages 存在于一个特定的 GitHub Pages 文件专有库中。你将使用用户名来命名这个库，比如 atmos/atmos.github.io。

你必须使用username.github.io这样的命名体制。
master分支上的内容将用于构建和发布你的 GitHub Pages 网页。
你只可以使用你自己的用户名创建用户或者组织 Pages 的库。像joe/bob.github.io这样的命名将不能构建用户 Pages 网站。

当用户 Pages 构建完之后，打开http(s)://<username>.github.io就可以正常使用了。

### 构建你的用户 & 组织 Pages

用户 Pages 的构建可以通过任何经过认证邮件的账户。它也可以使用 部署 keys 来自动化这个过程。

组织 Pages 的构建可以通过任何有 push 权限的成员和有认证邮件的用户。想要自动构建，你可以 设置一个机器用户 作为你的组织的成员。组织 Pages 不支持部署 keys。


### 项目 Pages
不像用户和组织的 Pages，项目 Pages 是作为一个项目保存在同一个库中。个人账户和组织都可以创建项目 Pages。个人账户的项目 Pages 的 URL将会是这样 http(s)://<username>.github.io/<projectname>，但组织的 URL 是http(s)://<orgname>.github.io/<projectname>。创建项目 Pages 的步骤两者都是相同的。

项目 Pages 与用户和组织 Pages 很相似，但有一些轻微的不同：

gh-pages分支用来构建和发布项目 Pages 网站。

如果没有 自定义的域名，项目 Pages 网站将服务在用户 Pages 网站的子域名下：username.github.io/projectname。

用户和组织 Pages 网站的 自定义域名 适用于这个账户托管的所有重定向项目 Pages 的相同域名。使用自定义域名的项目 Pages 网站同样在个人账户的username.github.io/projectname和组织的orgname.github.io/projectname中有效。

自定义的 404s 只用在使用了自定义域名的网站。否则，将使用用户 Pages 404。

## 用自动生成器生成 Pages
你可以使用 GitHub Pages 自动生成器快速的建立一个项目的网页、用户或组织的网页。

### 用户和组织 Pages
为了生成用户和组织的网页，你需要生成一个库叫作username.github.io。用户名和组织名必须是你自己的否则你的 GitHub Pages 不会建立的。页面自动生成器是容易通过库的设置页面进入的。你可以从这里阅读更多关于用户和组织页面。

警告： GitHub Pages 在互联网上是公开的可进入的，尽管它们的库是私有的。如果你有一些敏感的数据在你的页面库中，你可能想把它在发布前去除。

### 项目 Pages
你可以用页面自动生成器给任何项目库去发布 GitHub Pages。

警告：你必须新建一个符合命名规则描述的库，否则你将不能把它发布到你的 GitHub Pages。

### 页面自动生成器

1. 在 GitHub 上打开库的页面。
2. 在你的库右面的侧边栏，点击扳手图标。
3. 点击 Automatic Page Generator 按钮。
4. 编辑的的内容在 Markdown 编辑器。
5. 点击 Continue To Layouts 按钮。
6. 在主题中预览你的内容。
7. 当你找到你喜欢的主题，点击 Publish page。

在你的 GitHub Pages 生成之后，你可以得到它 HTML 代码的本地复制。如果你生成一个项目网页，fetch 和 check out 一个新的分支。

```
$ cd repository
$ git fetch origin
remote: Counting objects: 92, done.
remote: Compressing objects: 100% (63/63), done.
remote: Total 68 (delta 41), reused 0 (delta 0)
Unpacking objects: 100% (68/68), done.
From https://github.com/user/repo.git
* [new branch]      gh-pages     -> origin/gh-pages
$git checkout gh-pages
Branch gh-pages set up to track remote branch gh-pages from origin.
Switched to a new branch 'gh-pages'
```

如果你生成了一个用户网页，代码会在 master 的分支，而不是 gh-pages 的分支，所以仅仅 check out master然后 pull 就可以了。

```
$cd repository
$git checkout master
Switched to branch 'master'
git pull origin master
remote: Counting objects: 92, done.
remote: Compressing objects: 100% (63/63), done.
remote: Total 68 (delta 41), reused 0 (delta 0)
Receiving objects: 100% (424/424), 329.32 KiB | 178 KiB/s, done.
Resolving deltas: 100% (68/68), done.
From https://github.com/user/repo.git
 * branch      master     -> FETCH_HEAD
Updating abc1234..def5678
Fast-forward
index.html                                     |  265 ++++
...
98 files changed, 18123 insertions(+), 1 deletion(-)
create mode 100644 index.html
...
```

## 手动创建项目 Pages
如果你是熟悉 Git 的命令行的，手动创建项目 Pages 网站是非常直观易懂的。

### 做一个新的 clone
为了建立一个项目 Pages，你需要在你的库中新建一个新的 orphan 分支（一个与现存分支没有共同的历史的分支）。最安全的做法是从一个新的 clone 开始来做这件事：

```
$ git clone github.com/user/repository.git
# Clone our repository
Cloning into 'repository'...
remote: Counting objects: 2791, done.
remote: Compressing objects: 100% (1225/1225), done.
remote: Total 2791 (delta 1722), reused 2513 (delta 1493)
Receiving objects: 100% (2791/2791), 3.77 MiB | 969 KiB/s, done.
Resolving deltas: 100% (1722/1722), done.
```

### 新建一个 gh-pages 分支
一旦你拥有一个空的库，你将需要创建一个新的 gh-pages 分支且从工作目录和首页中去除所有的内容：

```
$ cd repository
$ git checkout --orphan gh-pages
Creates our branch, without any parents (it's an orphan!)
Switched to a new branch 'gh-pages'
$ git rm -rf .
Remove all files from the old working tree
rm '.gitignore'
```

提示：直到你第一次提交之前，gh-pages 分支不会出现在 git branch 生成的分支列表中。

### 添加内容和 push
当你 push 你的程序到页面库中，为了触发它构建，你必须首先验证你的邮箱地址。

现在你有一个空的工作目录。你可以在这个分支中创建一些内容和 push 它到 GitHub。例如：

```
$ echo "My Page" > index.html
$ git add index.html
$ git commit -a -m "First pages commit"
$ git push origin gh-pages
```

你的 GitHub Pages 应该是可用了。如果你建立的代码不成功，你将会收到一封邮件。

### 加载你的新 GitHub 网页
在你推送 gh-pages 分支后，你的项目 Pages 在http(s)://<username>.github.io/<projectname> 上是可用的。记住，这个 Pages 总是公开课进入的，当它发布之后，尽管它的库是私有的。

关于如何给 GitHub Pages 建立一个自定义的域名，可以看看给 GitHub 网页建立一个自定义的域名。

## Pages 中使用 Jekyll
除了支持常规的 HTML 内容之外，GitHub Pages 也支持 Jekyll，一个简单的，博客风格的静态网页生成器。Jekyll 使创建站点范围内的头部和底部变得简单，不需要在每个页面复制它们。它也提供一些其他更深入的模板功能。

### 使用 Jekyll
当你将内容推送到一个特别命名的分支版本库中运行，每个 GitHub Pages 是通过 Jekyll 处理。对于 User Pages，使用在 username.github.io 库的 master 分支。对于 Project Pages，使用项目中存储库中的 gh-pages 分支。因为一个普通的 HTML 网站也是一个有效的 Jekyll 网站，你不需要做什么特别的事情让您的标准 HTML 文件不变。 Jekyll 完整的文档，涵盖其功能和使用方法。只需启动提交 Jekyll 格式的文件，你就会在任何时间使用 Jekyll。

### 安装 Jekyll
我们强烈建议您的计算机上安装 Jekyll 预览您的网站，并在发布你的网站之前帮助检测出有问题的 GitHub Pages。

很幸运的是，在你的电脑上安装 Jekyll，并确保你的计算机最匹配 GitHub Pages 设置很容易，多亏了 the GitHub Pages Gem和我们的依赖版本的页面。要安装 Jekyll，你需要做几件事情：

1. **Ruby** - Jekyll 需要 Ruby 语言。如果你有一个苹果电脑，你很可能已经有 Ruby。如果你打开​​终端应用程序，然后运行命令ruby --version，可以证实这一点。你的 Ruby 版本至少应该是 2.0.0。如果你已经有了，你就已经完成这一步。跳至步骤 ＃2。否则，请按照以下说明安装 Ruby。

2. **Bundler** - 捆绑器的软件包管理器。它使 Ruby 软件版本像 Jekyll 一样。如果你将要在本地建设的 GitHub Pages，它能令你容易得多。如果你还没有安装 Bundler，你可以通过运行命令 gem install bundler 安装它。

3. **Jekyll** - 主要做的事。你将要创建一个名为 Gemfile 的文件在你的网站的库中并添加行 gem 'github-pages 。在此之后，只需运行命令，bundle install 就可以了。如果你决定跳过步骤＃2，你仍然可以使用命令 gem install github-pages 安装 Jekyll，但你可能会碰到了命令行的麻烦。这里有一个 Gemfile 的例子，你可以使用（放置在存储库的根目录）：

```
source 'https://rubygems.org'
gem 'github-pages'
```

### 运行 Jekyll
为了以符合 GitHub Pages 构建服务器的方式运行 Jekyll，需要通过 Bundler 运行 Jekyll。在库的根目录使用命令 bundle exec jekyll serve（在切换到项目库的 gh-pages 分支之后），然后应该能在 http://localhost:4000 访问你的网站。完整的 Jekyll 命令列表，请参见 Jekyll 文档。

### 保持 Jekyll 是最新的
Jekyll 是一个动态开源项目，它会频繁地更新。当 GitHub Pages 服务器更新了，在你电脑上的软件就会过时，导致你的网站出现本地和发布在 GitHub 的样子不一致。保持 Jekyll 的更新，你可以输入命令bundle（或者如果你选择跳开第二步，运行gem update github-pages）。

### 配置 Jekyll
你可以通过创建一个 _config.yml 来配置 Jekyll 大部分属性。

### 默认值

以下的默认值是 GitHub 设置的，你可以自由地重写 _config.yml 文件：

```
highlighter: pygments
github: [Repository metadata]
```

对于存储库的元数据对象的内容，请参阅 GitHub Pages 库的元数据。

### 配置重写

我们可以重写下面的 _config.yml 中你不可以配置的值：

```
safe: true
lsi: false
source: your top-level directory
```

记住，如果你改变了 source 的设置，你的页面可能不能正确地建立。 GitHub Pages 把源文件作为最高级别的库目录来考虑。

### Frontmatter 是必须的
Jekyll 需要 Markdown 文件有一个 front-matter 定义在所有文件之上。Front-matter 只是一系列的元数据，由三个破折号划定：

```
---
title: This is my title
layout: post
---

Here is my page.
```

如果你喜欢，你可以选择从你的文件中删除 Front-matter，但是你仍然需要这三个破折号：

```
---
---

Here is my page.
```

如果你的文件在 _posts 目录中，你可完全删除这些破折号。 希望获取更多信息可以查看 Jekyll 文档。

### 问题解决

如果你的 Jekyll 网站在你 push 它到 GitHub 后没有表现为合适的形式，在本地运行 Jekyll 对你检查错误很有用。为了做到这件事，你将会希望使用 Jekyll 的相同版本和其它依赖。

为了保证你的本地开发环境是使用 Jekyll 的相同版本和 GutHub 网站的依赖，一旦 Jekyll 安装了，你可以定期地运行命令gem update github-pages（或者bundle update github-pages如果使用Bundler）。更多的信息，请参看 GitHub Pages Gem 库。

如果你的页面并没有建立在你 push 到 GitHub 之后，请参看 GitHub Pages 建立失败问题解决。

如果你 Jekyll 网页正在出现问题，请确定你没有使用和其它项目相同名字的分类，这个会引起路径冲突。例如，你有一个博客站点叫“简历”在你的用户网页库中，和一个项目名叫“简历”也有一个 gh-pages 的分支，它们会引起双方的冲突。

### 关闭 Jekyll
你可以通过在页面库的根目录下创建一个名为 .nojekyll 的文件并将其 push 到 GitHub 来完全退出 Jekyll。只有当您的站点使用以下划线开头的目录，这才是必要的。Jekyll 把这些当作特殊的目录，并且不将它们复制到最终目的地。

### 贡献
如果你希望 Jekyll 拥有某些功能，请自由地 fork，并发送一个 pull 请求。我们很高兴接受到用户的意见。

## 关于 GitHub Pages 的自定义域名
有两种自定义域名可用于重定向 GitHub Pages：子域名和顶级域名（apex domains）。

### 子域名
一个子域名通过您的 DNS 提供商来配置 CNAME 记录。

我们因为以下这些原因强烈建议您使用自定义子域名：

它把我们内容分发网络的好处带给你的 GitHub Pages。
它不会受到 GitHub 服务底层 IP 地址变化影响。
Pages 将加载得更加快，因为拒绝服务保护可以更有效地实施。
### 顶级域名
一个顶级域名通过你的 DNS 供应商配置一个 A、ALLAS 或者 ANAME，和经常被分配给一个或更多的 IP 地址。

注意：一些 DNS 供应商支持配置顶级域名的 ALIAS 或者 ANAME 记录，但是没有专门的工业标准。一些 DNS 供应商（像 DNSimple ）允许顶级域名配置 ALIAS 或者 ANAME 指向其它域。

对于你的 GitHub Pages，我们推荐使用一个自定义的子域名，而不是一个顶级域名。

GitHub Pages 怎样使用自定义域名

| GitHub Pages 种类 | GitHub 的主机位置 | 页面是怎么重定向的 | 自定义域名例子 |
| --- | --- | --- | --- |
| 用户 Pages | username.github.io | 自动重定向至已经设定好的自定义域名 | user.example.com |
| 组织 Pages | orgname.github.io | 自动重定向至已经设定好的自定义域名 | org.example.com |
| 用户账号拥有的项目 Pages | username.github.io/projectname | 自动重定向到一个由用户指定的，用户网站自定义域名的子目录（ user.example.com/projectname），以及所有自定义域名 | project.example.com |
| 组织拥有的项目 Pages | orgname.github.io/projectname | 自动重定向到一个由组织指定的，项目 Pages 自定义域名的子目录(org.example.com/projectname)，以及所有自定义域名 | project.example.com |

解决自定义域的问题，可以参考“我的自定义域出现问题了。

## 设置 GitHub Pages 的自定义域名
你可以为用户、组织和项目 Pages 配置一个自定义域名。

获取在不同类型的自定义域名信息，可以参看关于 GitHub 网站的自定义域。

### 新建和上传一个 CNAME 文件
为了重定向你的 GitHub Pages，你必须新建和上传一个 CNAME 文件。这个文件包含你的库根目录的自定义域名。更多资讯，请参看为你的库添加一个 CNAME 文件。

### 通过你的 DNS 提供商配置自定义子域名
如果你的自定义域名是一个子域名，你必须通过你的 DNS 提供商配置 CNAME 记录。欲了解更多信息，请参见通过你的 DNS 提供商配置 CNAME 记录的技巧。

### 通过你的 DNS 提供商配置自定义顶级域名
如果你的自定义域名是一个顶级域名，你必须配置 ALIAS 、ANAME 或通过 DNA 提供商配置 A 记录，欲了解更多信息，请参见通过你的DNS提供商配置 A 记录的技巧。

## 在 DNS 提供者上配置 CNAME 记录的技巧
要设置一个自定义子域名，你必须要在你的 DNS 提供者上配置一个 CNAME 记录，这可能会或可能不会和你的网络主机提供者相同。

要获取更多自定义子域名的信息，可详见“关于 GitHub 网页站点的自定义域.”。

提示：你可以仅仅只为 GitHub Pages 配置一个自定义域名或者一个自定义顶级域名，除非你使用了一个 www 的子域名。

### 在 DNS 提供者上配置自定义子域名
与你的 DNS 提供者一起，创建一个 CNAME 记录指的是从该域到 username.github.io。DNS 的变化会占用一整天去扩散蔓延。

不要在 GitHub Pages 中使用通配符 DNS 记录（例如 *.example.com ）！一个通配符 DNS 记录可以让任何人在其中一个子域名中登录到 GitHub Pages。

为确保你的 CNAME 记录设置正确，使用 dig 命令：

```
$ dig www.example.com +nostats +nocomments +nocmd  
;www.example.com.                     IN      A
www.example.com.              3592    IN      CNAME   username.github.io.
username.github.io.           43192   IN      CNAME   github.map.fastly.net.
github.map.fastly.net.        22      IN      A       199.27.76.133
```

### 配置一个 www 子域名
如果你配置一个顶级域名（例如 example.com ）和一个匹配的 www 子域名（例如 www.example.com ），GitHub 服务器会自动地创建双重定向。

例如：

如果你的 CNAME 文件包含 example.com，那么 www.example.com 会定向到 example.com。
如果你的 CNAME 文件包含 www.example.com，那么 example.com 会定向到 www.example.com。
你可以使用除了 www 以外的一个自定义子域名和一个自定义顶级域名来通过域名重定向（有时候也叫“域名转发”）。但是，请注意，这只能用于用户和组织的 Pages，而不是项目的 Pages。



## 添加 CNAME 文件到你的存储库中
如果你正在使用一个自定义域名去重定向你的 GitHub Pages，你必须创建和提交一个包含自定义域名的 CNAME 文件到你的 GitHub Pages 存储库中。

1. 在 GitHub，导航到你的页面存储库。
2. 在“分支”菜单中，切换到你存储库的Pages 分支：
    * 对于用户和组织的页面站点来说，Pages 分支是 master 。
    * 对于项目页面站点来说，Pages 分支是 gh-pages 。
5. 添加一个新文件，命名为 CNAME （全部大写！），放在 Pages 分支的根目录下。
6. 在新文件中，添加一行，指定自定义域名的空子域名。例如，使用 blog.example.com 而不是 https://blog.example.com 。请注意，在 CNAME 文件中只允许有一个域名。
7. 输入提交的消息，或接受默认消息。
8. 在提交消息的对话框底部，点击 Confirm merge。
### 确认自定义域名配置正确
在你的存储库右边侧边栏，点击扳手图标.

在“ GitHub Pages ”底部，你会看到你的 CNAME 文件的自定义域名。


### 下一步：配置 DNS 的设置项
在你已经创建和提交你的 CNAME 文件到 GitHub 之后，在你的 DNS 提供者上做以下项之一：

如果你的自定义域是一个子域名（推荐），配置一个 CNAME 记录。
如果你的自定义域是一个顶级域名，配置一个 ALIAS , ANAME ,或者 A 记录。
真实的 CNAME 文件例子
**atmos.github.io repository** 有一个域名为 www.atmos.org 的 CNAME 文件。

用户 Pages 站点 atmos.github.io 定向到 www.atmos.org。
项目 Pages 站点 atmos.github.io/warden-github 定向到 www.atmos.org。
注意项目 Pages 站点如何继承其所有者的用户 Pages 站点的域。

**emoji repository**有一个域名为 emoji.muan.co 的 CNAME 文件。它归 muan 所有，muan 的用户 Pages 存储库有一个域名为 muan.co 的 CNAME 文件。

项目 Pages 站点 muan.github.io/emoji 定向到 muan.co/emoji，这对于 emoji.muan.co 也同样适用。
进一步了解
“在 GitHub 页面上设置一个自定义域”

## 在你的 DNS 提供者上配置 A 记录的技巧
要设置一个自定义顶点域名，你必须要在你的 DNS 提供者上配置一个 ALIAS，ANAME ，或者 A 记录，这可能会或者可能不会和你的网络主机提供者相同。

警告：不要在你的 DNS 提供者上为你的自定义顶点域名创建一个 CNAME 记录！这样做可能会导致与其他服务，如电子邮件，在该域的问题。

要获取更多的自定义顶点域信息，详见“关于 GitHub 页面站点的自定义顶点域名”

提示：你可以仅仅只为 GitHub Pages 站点配置一个自定义子域名或者一个自定义顶点域名，除非你使用一个 www 子域名。

在你的 DNS 上配置一个 A 记录
在你的 DNS 提供者上，创建 A 记录来解决以下的IP地址：

* 192.30.252.153
* 192.30.252.154

为了确保你的 A 记录设置正确，使用 dig 命令：

```
$ dig example.com +nostats +nocomments +nocmd
;example.com
example.com.   73  IN  A 192.30.252.153
example.com.   73  IN  A 192.30.252.154
```

在你的 DNS 提供者上配置一个 ALIAS 或者一个 ANAME 记录
如果你的 DNS 提供者支持 ALIAS 记录（例如是 DNSimple ）或者 ANAME 记录（例如是 DNS Made Easy ），你可以选择创建一个 ALIAS 记录或者一个 ANAME 记录来代替 username.github.io。

注意：一些 DNS 提供者允许顶点域名配置一个 ALIAS 记录指向其他的域名。

为了确保你的 ALIAS 或者 ANAME 记录设置正确，使用 dig 命令：

```
$ dig example.com +nostats +nocomments +nocmd
example.com.     3600    IN A     199.27.XX.XXX
```

在这里显示的 IP 地址必须要和 dig username.github.io 所显示的最终的 IP 地址相匹配。

配置一个 www 子域名
如果你配置一个顶点域名（例如 example.com ）和一个匹配的 www 子域名（例如 www.example.com ），GitHub 服务器会自动的创建两重定向。

例如：

如果你的 CNAME 文件包含 example.com，那么 www.example.com 会定向到 example.com。

如果你的 CNAME 文件包含 www.example.com，那么 example.com 会定向到 www.example.com。
你可以使用除 www 以外的一个自定义子域名和一个自定义顶级域名一起通过域名重定向（有时也称为“域名转发”）。但是，请注意，这仅仅只用于用户和组织的页面，而非项目页面。


## 进一步了解 GitHub Pages
详见“ GitHub Pages Features ”来获取更多关于 GitHub Pages 站点上使用已批准的 Jekyll 插件，创建自定义 404 页面和查看可用的存储元数据的信息。

详见“ GitHub Pages Troubleshooting ”来帮助排除自定义域名的问题和常见故障，还有取消发布你的 GitHub Pages 站点的步骤。


