

# MkDocs项目文档生成器(一)

## 简介

#### 介绍 

项目文档生成器，生成静态站点，管理MarkDown文档；

#### 官网

[英文官网](http://www.mkdocs.org/) [中文官网](https://markdown-docs-zh.readthedocs.io/zh_CN/latest/)  `建议直接看最新的英文官方文档`

#### 特点

- 一个用于创建项目文档的快速、简单、华丽的静态站点生成器，文档源码使用 Markdown 来撰写，用一个 YAML 文件作为配置文档。
- 构建完全静态的 HTML 站点，可以将它托管到 GitHub pages、Amazon S3 等任意地方。
- 默认包含大量美观的主题，可以在内置主题：mkdocs和readthedocs之间进行选择，也可以在MkDocs wiki中选择任一第三方主题，或者构建自己的主题。
- 即时预览。

```java
  内建服务器允许我们在编写文档时预览文档。
  每当我们保存更改时，其甚至会自动重新加载并刷新我们的浏览器。
```

- 易于配置。

```java
  通过自定义主题，让我们的项目文档以我们希望的方式查找。
```

- 交叉索引。

## 安装(MacOS)

- ##### `brew search mkdocs` 搜索Homebrew Cask中是否存在mkdocs

- ##### `brew install mkdocs` 安装MkDocs

- #####  `mkdocs --version` 验证安装

## 使用

#### 初步试用

根据官方文档的步骤创建和使用MkDocs `建议先看中文文档了解过程，然后根据官方文档操作，因为官方文档总是最新的。`

#### 常用命令

- `mkdocs --help` 帮助

```java
  mkdocs 指定命令 --help - 查看给定命令上可用的选项列表。
  eg.mkdocs new --help - 查看新建工程命令上可用的选项列表。
```

- `mkdocs new '工程名'` 创建新的MkDocs工程
- `mkdocs serve` 运行内建的开发服务器
- `mkdocs build` 构建MkDocs文档
- `mkdocs gh-deploy` 将文档部署到GitHub页面上
- `mkdocs json` 将MkDocs文档构建成JSON文件

```java
注*
以上命令除创建新的MkDocs命令外，均须在工程目录下执行。
```

#### 操作流程

1.创建工程 - `mkdocs new MkDocs`

```java
花一点时间来回顾一下我们创建的初始项目:
有一个名为mkdocs.yml的配置文件，以及一个名为docs的文件夹，里面是我们文档的源文件。现在，该docs文件夹只包含一个名为index.md的文档页面。
MkDocs附带一个内建服务器，可以让我们在处理文档时预览文档。确保我们与mkdocs.yml配置文件位于同一目录中，然后启用内建服务器：
```

2.启用内建服务器 - `mkdocs serve`

```java
➜  MkDocs git:(master) ✗ mkdocs serve
INFO    -  Building documentation...
WARNING -  Config value: 'pages'. Warning: The 'pages' configuration option has been deprecated and will be removed in a future release of MkDocs. Use 'nav' instead.
INFO    -  Cleaning site directory
[I 190725 14:56:46 server:292] Serving on http://127.0.0.1:8000
[I 190725 14:56:46 handlers:59] Start watching changes
[I 190725 14:56:46 handlers:61] Start detecting changes
[I 190725 14:56:46 handlers:132] Browser Connected: http://127.0.0.1:8000/
[I 190725 14:56:47 handlers:92] Reload 1 waiters: None
[I 190725 14:56:47 handlers:132] Browser Connected: http://127.0.0.1:8000/
[I 190725 14:56:48 handlers:79] Ignore: /usr/local/Cellar/mkdocs/1.0.4_1/libexec/lib/python3.7/site-packages/mkdocs/contrib/search/templates/search/lunr.js
```

3.[在浏览器中打开](http://127.0.0.1:8000/)我们将看到显示的默认主页：

```java
内建服务支持自动重新加载，只要配置文件、文档目录或主题目录中的任何内容发生更改，都将重建文档。
现在尝试编辑mkdocs.yml配置文件：将site_name值更改为MyMkdocs并保存。
我们的浏览器将自动重新加载，我们应该立即看到更新过的文档 - 新的站点名称生效。
```

4.添加页面

- 现在在文档中添加第二页（about.md）：

- 由于我们的文档站点将包含一些导航标题，因此可能需要编辑配置文件，并通过添加`pages`设置在导航标题中添加有关每个页面的顺序、标题和嵌套的一些信息：

```java
  site_name: My MkDocs
  pages:
  - 首页: index.md
  - 关于: about.md
```

- 保存更改，现在我们会看到位于导航栏左侧的`主页`和`关于` 菜单项左侧以及位于导航栏右侧的`Search`，`Previous`和`Next`菜单项。

- 尝试菜单项并在页面之间来回导航。然后点击 `Search`。将出现一个搜索对话框，允许我们搜索任何页面上的任何文本。

```java
  请注意，搜索结果包括网站上每次出现的搜索字词，并直接链接到搜索字词所在页面的部分。我们无需付出任何努力或配置即可完成所有这些工作！
```

5.配置主题

- 现在在配置文件中更改主题以更改文档的显示方式。编辑`mkdocs.yml`文件并添加theme设置：

```java
  site_name: My MkDocs
  pages:
  - 主页: index.md
  - 关于: about.md
  theme: readthedocs
```

- 保存更改，我们将看到正在使用的readthedocs主题

6.更改favicon图标

```java
默认情况下，MkDocs使用MkDocs favicon图标。
要使用其他图标，须在我们的docs目录下创建img子目录，然后将自定义favicon.ico文件复制到该目录。
MkDocs将自动检测并使用该文件作为我们的的favicon图标。
```



7.生成站点 - `mkdocs build`

至此，我们已经准备好部署My MkDocs文档的第一个过程。

- 首先构建文档

```java
	mkdocs build
```

- 这将创建一个名为`site`的新目录。看一下目录：

```java
  ➜  site git:(master) ✗ tree -L 2
  .
  ├── 404.html
  ├── about
  │   └── index.html
  ├── css
  │   ├── base.css
  │   ├── bootstrap-custom.min.css
  │   └── font-awesome.min.css
  ├── fonts
  │   ├── fontawesome-webfont.eot
  │   ├── fontawesome-webfont.svg
  │   ├── fontawesome-webfont.ttf
  │   ├── fontawesome-webfont.woff
  │   ├── fontawesome-webfont.woff2
  │   ├── glyphicons-halflings-regular.eot
  │   ├── glyphicons-halflings-regular.svg
  │   ├── glyphicons-halflings-regular.ttf
  │   ├── glyphicons-halflings-regular.woff
  │   └── glyphicons-halflings-regular.woff2
  ├── img
  │   ├── favicon.ico
  │   ├── grid.png
  │   └── index
  ├── index.html
  ├── js
  │   ├── base.js
  │   ├── bootstrap-3.0.3.min.js
  │   └── jquery-1.10.2.min.js
  ├── search
  │   ├── lunr.js
  │   ├── main.js
  │   ├── search_index.json
  │   └── worker.js
  ├── sitemap.xml
  └── sitemap.xml.gz
  请注意，我们的源文档已输出为两个名为index.html和about/index.html的HTML文件。
  我们还有各种其他媒体已作为文档主题的部分复制到site了目录中。
  我们甚至有一个sitemap.xml文件和mkdocs/search_index.json。
```

- 如果我们正在使用源代码控制，例如`git`；我们可能不希望将文档构建检查添加到存储库中。因此添加包含 `site/`的行在我们的`.gitignore`文件中。

```java
	echo "site/" >> .gitignore
```

- 一段时间后，文件可能会从文档中删除，但它们仍将驻留在`site`目录中。要删除这些陈旧文件，只需`mkdocs` 使用`--clean`开关运行即可。

```java
	mkdocs build --clean
```

8.其它命令和选项

- 还有其他各种命令和选项。有关命令的完整列表，请使用`--help`标志：

```java
	mkdocs --help
```

- 要查看给定命令上可用的选项列表，请使用带该命令标志的`--help`。例如，要获取该`build`命令可用的所有选项的列表，请运行以下命令：

```java
	mkdocs build --help
```

9.部署

- 我们刚刚构建的文档站点仅使用静态文件，因此我们几乎可以在任何地方托管它。
- [GitHub项目页面](https://help.github.com/articles/creating-project-pages-manually/)和[Amazon S3](https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteHosting.html)可能是很好的托管选项（具体取决于我们的需求）。
- 将整个`site`目录的内容上传到您托管网站的任何地方，然后我们就完成了（有关许多常见主机的具体说明，请参阅[部署您的文档](https://www.mkdocs.org/user-guide/deploying-your-docs/)页面）。

```java
注*：
	1. 如果是公司的项目，项目文档不能对外开放，我们可以上传到公司的GitLab上。
	2. 如果是个人的项目，我们可以上传到GitHub上
```

## 注意

- ##### 如果创建站点的话，将图片和文档放在同一个文件夹中即可。
- ##### 如果是图片的话，需要重启本地内置的服务器。
- ##### 内建服务器支持在配置文件、文档目录或主题发生改变时自动载入并重新生成文档。

# MkDocs项目文档生成器(二)

## 前言

前面一篇讲了如果搭建自己的MkDocs来管理自己的文档，在搭建完成后既可以使用内设的小型服务器来生成一个静态的站点、又可以将我们的site文件夹直接放到服务器上；

```java
eg.
放在本地的Tomcat: apacht-comcat-8.0.36\webapps路径下，启用自己的Tomcat，就能够直接访问：http://ipaddress:8080/site/，就会默认打开site目录下的index.html。
同理，我们也可以将其放到自己公司的服务器或者托管到GithubPages上；
```

## 项目发布到GitHub Pages

1. 创建名为`username.github.io`的空`repository`
2. 将仓库`clone`到本地
3. 将mkdocs文档生成的site文件夹下的所有内容复制到本地的仓库中并`push`到github上
4. 访问`username.github.io`，默认就会打开仓库的根目录下的index.html这个网页 - 恭喜你，大功告成！

## 编辑

- 配置页面和导航栏（在mkdocs.yml配置文件中定义的页面才会被mkdocs创建，然后显示在导航栏上）

```java
    简单的配置页面：

    pages:
    - 首页: index.md
    - 关于: about.md
```

- 多级导航栏（按照下面的代码创建的子选项会被以列表的形式，显示在所属的导航条下）

```java
    pages:
    - 首页: index.md
    - 用户指南:
        - 编辑你的文档: user-guide/writing-your-docs.md
        - 设计你的文档: user-guide/styling-your-docs.md
    - 关于:
        - 许可证: about/license.md
        - 发行说明: about/release-notes.md
```

- 文件的路径（如果MarkDown文件是在一个site中，那么文档的URL就是文档的路径）

```java
    docs/
        index.md
        user-guide/getting-started.md
        user-guide/configuration-options.md
        license.md
        getting-started.md这个文档的路径就是user-guide/getting-started.md，默认根目录就是docs
        这样的话，就可以在一个文档中链接另外一个文档了，即可以从文档A中打开文档B，见下面的内容。
```

- 内部链接（从一个文档中打开另外一个文档）

```java
    [如何开始构建文档](user-guide/getting-started.md)
    其实最后会被转化成从一个网页打开另外一个网页
```

- 显示图片（路径如下：）

```java
    mkdocs.yml
    docs/
        CNAME
        index.md
        about.md
        license.md
        img/
            screenshot.png
            
    在MarkDown中写法如下，其实这个就是markdown的标准语法，圆括号中的就是图片的地址，可以是本地的地址，也可以是网络的地址：
    ![Screenshot](img/screenshot.png)
```

- MarkDown语法扩展


```java
	推荐一个十分不错的MarkDown软件Typora
```

## 样式

MkDocs包含许多不同的内置的样式和扩展的样式，也可以很容易的实现个性定制

- ##### 想要使用内置的样式，只要在配置文件中写入下列代码：

```java
    theme: readthedocs
    即 theme: 样式的名称
```

- ##### 目前可用的样式包括mkdocs和readthedocs两种

  ![mkdocs主题](https://raw.githubusercontent.com/MoeRookie/MkDocs/master/docs/img/index/mkdocs主题.png)
  
  ![readthedocs主题](https://raw.githubusercontent.com/MoeRookie/MkDocs/master/docs/img/index/readthedocs主题.png)

```java
其它几个主题需要安装，因为不会附带，但是安装的时候提示升级，升级的时候提示错误，所以我就忽略了，重点在文档的内容，主题什么的以后再说吧！
```

## 配置

下面给出部分主要的配置信息：

#### 项目信息

- ##### `site_name` 站点的名称，这个配置是必须的，并且会显示在网页的顶部

```java
	site_name: The Library of Development
```

- ##### `site_description` 站点的描述

```java
	配置信息太多了，可以查看中文文档的翻译，然后从官方网站上复制代码
```

