# Blizzard's Blog

这是个人博客仓库，使用 Jekyll + Chirpy 主题构建，通过 GitHub Actions 发布到 GitHub Pages。

博客地址：

```text
https://cat-blizzard.github.io/blog/
```

仓库地址：

```text
https://github.com/Cat-blizzard/blog
```

## 站点类型

这个仓库是 GitHub Pages 的项目站点，不是个人主页仓库。

因此 `_config.yml` 里必须保持：

```yaml
url: "https://cat-blizzard.github.io"
baseurl: "/blog"
```

如果仓库名不是 `blog`，`baseurl` 也要跟着改成对应的仓库名，例如仓库名是 `notes`，就写：

```yaml
baseurl: "/notes"
```

## 常用文件

- `_config.yml`：站点标题、副标题、作者、邮箱、GitHub 用户名、站点地址、评论、统计等配置。
- `_posts/`：博客文章目录。
- `_tabs/about.md`：About 页面内容。
- `_data/contact.yml`：左侧栏联系方式。
- `assets/`：图片和其他静态资源。
- `.github/workflows/pages-deploy.yml`：GitHub Actions 自动构建和部署流程。

## 写一篇新文章

文章放在 `_posts/` 目录。

文件名格式：

```text
YYYY-MM-DD-title.md
```

例如：

```text
_posts/2026-06-09-my-note.md
```

文章开头需要写 front matter：

```yaml
---
title: 我的文章标题
date: 2026-06-09 20:00:00 +0800
categories: [Blog]
tags: [chirpy, github-pages]
---
```

然后在下面正常写 Markdown 内容。

## 发布更新

在本地仓库目录执行：

```powershell
cd D:\Blog
git status
git add .
git commit -m "Update blog"
git push
```

推送后，GitHub Actions 会自动构建并发布网站。

Actions 页面：

```text
https://github.com/Cat-blizzard/blog/actions
```

## GitHub Pages 设置

仓库需要使用 GitHub Actions 作为 Pages 来源：

```text
Settings -> Pages -> Build and deployment -> Source -> GitHub Actions
```

如果 Actions 在 `Setup Pages` 步骤失败，优先检查这里是不是已经选成 `GitHub Actions`。

## 本地预览

当前这台机器没有安装 Ruby/Bundler，所以本地暂时不能直接运行 Jekyll 预览；推送到 GitHub 后可以由 GitHub Actions 构建。

如果以后安装了 Ruby，可以用：

```powershell
bundle install
bundle exec jekyll serve
```

然后打开：

```text
http://127.0.0.1:4000/blog/
```

## 日常管理建议

- 写文章只改 `_posts/`。
- 改个人介绍只改 `_tabs/about.md`。
- 改站点标题、邮箱、头像、评论等全局信息时改 `_config.yml`。
- 不要随便改 `.github/workflows/pages-deploy.yml`，除非 GitHub Actions 构建流程需要调整。
- `baseurl: "/blog"` 不要删掉，否则项目站点的 CSS、JS 和文章链接可能会失效。
