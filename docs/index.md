

# MkDocs项目文档生成器(一)

## 简介

#### 介绍 

项目文档生成器，生成静态站点，管理MarkDown文档；

#### 官网

[英文官网](http://www.mkdocs.org/) [中文官网](https://markdown-docs-zh.readthedocs.io/zh_CN/latest/)  `建议直接看最新的英文官方文档`

#### 特点

- 一个用于创建项目文档的快速、简单、华丽的静态站点生成器，文档源码使用 Markdown 来撰写，用一个 YAML 文件作为配置文档。
- 构建完全静态的 HTML 站点，可以将它托管到 GitHub pages、Amazon S3 等任意地方。
- 默认包含大量美观的主题，可以从 bootstrap, readthedocs 和 12 款 bootswatch 主题中选择。
- 即时预览。
- 易于配置。
- 交叉索引。

## 安装

- ##### `brew search mkdocs` 搜索Homebrew Cask中是否存在mkdocs

- ##### `brew install mkdocs` 安装MkDocs

- #####  `mkdocs --version` 验证安装

## 使用

#### 初步试用

根据官方文档的步骤创建和使用MkDocs `建议先看中文文档了解过程，然后根据官方文档操作，因为官方文档总是最新的。`

#### 常用命令

- `help` 帮助 `指定命令 --help : 查看给定命令上可用的选项列表。`

- `new` 创建新的MkDocs工程

- `serve` 运行内建的开发服务器

- `build` 构建MkDocs文档

- `gh-deploy` 将文档部署到GitHub页面上

- `json` 将MkDocs文档构建成JSON文件

#### 操作流程

1.创建工程 - `mkdocs new 工程名`

2.启用内建服务器 - `mkdocs serve`

3.在浏览器中打开 - `http://127.0.0.1:8000/`

4.添加头部导航条

4.1. 在mkdocs.yml中修改site_name为指定内容

4.2. 在mkdocs.yml中配置导航条

- 在docs目录下新建about.md

-  .yml配置文件内容如下

```java
   site_name: My MkDocs
   pages:
   - 首页: index.md
   - 关于: about.md
```

5.配置主题

```java
在mkdocs.yml中添加主题
theme: readthedocs
```

6.生成站点 - `mkdocs build`

- ##### 如果你使用 git 等版本控制系统，你可能不希望提交构建之后的文档到版本库，在 .gitignore 中添加site/即可忽略该目录`echo "site/" >> .gitignore`

- ##### 一段时间后，可能有文件被从源码中移除了，但是相关的文档仍残留在 site 目录中。而在构建命令中添加--clean参数即可移除这些文档`mkdocs build —clean`

7.发布

1. ##### MkDocs 生成的文档只包含静态文件，因此你可以将文档部署到任意地方。GitHub project pages 和Amazon S3 是不错的选择，只需上传 site 目录到你需要发布的位置即可。
2. ##### 如果是公司的项目，项目文档不能对外开放，你可以上传到公司的GitLab上。
3. ##### 如果是个人的项目，你可以上传到GitHub上。

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

