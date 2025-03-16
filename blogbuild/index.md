# 博客搭建

# 前言
第一次搭建博客，仍有诸多不完善的地方

# 常用的hugo命令

创建一篇新文章
```bash
cd /d/hugo/KieranKaiyanLiang
hugo new posts/xxx.md
```
当编辑完文字后
使用bash脚本一键部署
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

# 获取变更文件列表（最多显示前10个文件避免信息过长）
CHANGES=$(git diff --cached --name-only | head -n 10 | tr '\n' ' ')

# 提交并推送（强制覆盖）
git commit -m "Update: $CHANGES...[其他变更省略]" || exit 1
git push --force origin master || exit 1

echo "部署成功！"
```
