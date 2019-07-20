---
title: "开始使用hugo"
date: 2019-07-20T10:34:00+08:00
categories: ["hugo","golang"]
tags: ["hugo","golang"]
toc: true
draft: false
---

工作了这么长时间，一直都没有写blog的习惯，基本都是将笔记记录到了有道云笔记和onenote中。作为golang的新用户，最近沉迷于golang无法自拔，golang在并发编程的代码书写效率极高。
并且前段时间将公司的缓存系统，统一从redis迁移到了codis，非常方便进行运维、扩容、监控。
于是看了一下codis的源代码，codis的架构设计还是非常完善的，因此想写文章记录一下源码阅读的过程，从而发现了hugo。


## 什么是hugo

> Hugo is a fast and modern static site generator written in Go, and designed to make website creation fun again. 
>
> Hugo 是一个Go写的静态网站生成工具，速度快，扩展性强。

## 为什么选择hugo

    * 快！世界上最快的静态网站生成工具！5秒生成6000个页面！
    * 超详细的文档，虽然是英文的
    * 活跃的社区
    * 更加自由的内容组织方式
    * 丰富的主题，目前主题数量已经超过 Hexo

更多介绍请查看官网，https://gohugo.io/

## hugo的安装

#### mac 平台

mac 下面提供了homebrew的安装方式

```shell
brew install hugo
```

#### Windows 平台

```shell
# 前往 https://github.com/gohugoio/hugo/releases
# 下载 hugo_X.XX_Windows-64bit.zip
# 解压得到 hugo.exe
# 将 hugo.exe 所在目录添加至系统环境变量
# 安装完成！
```

#### Debian 和 Ubuntu 平台

```shell
sudo apt-get install hugo
```

验证安装是否成功

```shell
hugo version
```

其他系统请参考[官方文档——安装](https://gohugo.io/getting-started/installing/)

### hugo的使用

#### 创建站点

```shell
hugo new site blog
```

#### 添加一个主题

```shell
cd blog
git init
git submodule add https://github.com/budparr/gohugo-theme-ananke.git themes/ananke

# 编辑你的 config.toml 配置文件使用该主题
echo 'theme = "ananke"' >> config.toml
```

#### 添加一篇文章

```shell
hugo new post/first-post.md
```

编辑 first-post.md

```shell
# 将draft: true，调整为
draft: false
```

#### 运行服务器查看效果

```shell
hugo server -D
```

然后打开浏览器，访问http://localhost:1313/ 就可以查看新创建的站点了。





### 配置hugo

#### 配置文章地址格式

编辑config.toml，添加如下配置

```shell
[permalinks]
  post = "/:year/:month/:filename"
# 所有可用的属性如下
# /:monthname/:day/:weekday/:weekdayname/:yearday/:section/:title/:slug/:filename/
```

这个时候生成的地址格式为 `/2019/07/20/hugo-start/ ` ，如果希望生成的地址为 `/2019/07/20/hugo-start.html`，config.toml添加如下配置：

```shell
uglyurls = true
```

完整配置文件请参考  https://gohugo.io/getting-started/configuration/#toml-configuration



### 使用 Hugo maupassant主题



```bash
cd <YOUR Bolg Root Dir>
git clone https://github.com/rujews/maupassant-hugo themes/maupassant
```

然后在Hugo的配置文件里config.toml(yaml,json)中进行如下配置，即可使用。

```toml
theme = "maupassant"
```

​	主题详细配置请查看 https://github.com/rujews/maupassant-hugo

