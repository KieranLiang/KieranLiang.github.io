# 博客搭建


# 前言

第一次搭建博客，仍有诸多不完善的地方

# 快速开始

创建一篇新文章

```bash
cd /d/hugo/KieranKaiyanLiang
hugo new posts/xxx.md
```

此时会在KieranKaiyanLiang/content/posts下创建xxx.md文档

当编辑完文字后，运行脚本auto_deploy.sh一键部署

```bash
#!/bin/bash

# 进入 Hugo 项目目录（注意 WSL 的路径格式）
cd /d/hugo/KieranKaiyanLiang || { echo "无法进入项目目录"; exit 1; }

# 生成静态文件
hugo || { echo "Hugo 生成失败"; exit 1; }

# 进入 public 目录
cd public || { echo "无法进入 public 目录"; exit 1; }

# Git 操作
git add . || exit 1

# 提交并推送（强制覆盖）
git commit -m "Auto-update: $(date +'%Y-%m-%d %H:%M')"
git push --force || exit 1

echo "部署成功！"
#否则终端会自动关闭看不清运行结果
read -p "按回车关闭终端"  
```

# 新建文章
hugo new posts/xxx.md命令能够根据archetypes/default.md中的配置初始化md文档

主要就是初始化文章的Front Matter

![image-20251018045828856](https://gitee.com/kieranliang/typora-image/raw/master/typora/2025-10-18/57db1dd85b4b69a06cfd6328a53774ed.png)

Front Matter还可以设置下列选项：
| 字段               | 作用       | 示例                                         |
| ---------------- | -------- | ------------------------------------------ |
| `title`          | 文章标题     | `{{ replace .File.ContentBaseName "-" " " \| title }}` |
| `date`           | 发布时间     | `date: {{ .Date }}`                        |
| `draft`          | 是否草稿     | `draft: true`                              |
| `slug`           | URL 别名   | `slug: my-first-post`                      |
| `url`            | 页面完整 URL | `url: /posts/my-first-post/`               |
| `description`    | 摘要       | `description: "文章摘要"`                      |
| `categories`     | 分类       | `categories: ["Tech", "Hugo"]`             |
| `tags`           | 标签       | `tags: ["hugo", "markdown"]`               |
| `author`         | 作者       | `author: "Kieran"`                         |
| `featured_image` | 封面图      | `featured_image: "/images/post-cover.jpg"` |
| `layout`         | 使用模板     | `layout: post`                             |
| `publishDate`    | 实际发布时间   | `publishDate: 2025-10-18`                  |


但其实直接在content/posts下手动创建md文档也可以

# 
