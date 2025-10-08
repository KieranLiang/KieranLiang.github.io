# 博客搭建


# 前言

第一次搭建博客，仍有诸多不完善的地方

# 常用的hugo命令

创建一篇新文章

```bash
cd /d/hugo/KieranKaiyanLiang
hugo new posts/xxx.md
```

此时会在KieranKaiyanLiang/content/posts下创建xxx.md文档

当编辑完文字后
运行脚本auto_deploy.sh一键部署

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

