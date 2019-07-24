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

```
   site_name: My MkDocs
   pages:
   - 首页: index.md
   - 关于: about.md
```

5.配置主题

```
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

## 编辑

## 样式

## 配置