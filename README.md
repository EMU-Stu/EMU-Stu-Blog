# EMU-Stu-Blog

本仓库是 [EMU-Stu 官网](https://emu-stu.github.io/blog) 的**博客文章**内容仓库，欢迎你的投稿！

无论是日常开发中折腾出的实战记录、比赛科研的避坑指南，还是对开源技术的深度探索，都欢迎你来分享。PR 合并后，文章会在几分钟内自动部署到官网。

## 目录结构

```
.
├── articles/
│   ├── my-article.md           文章正文（Markdown），文件名即 URL slug
│   └── images/                 文章引用的图片资源（统一放这里）
└── .github/workflows/
    └── notify-main-site.yml    push 后自动通知主仓库重新构建部署
```

## 投稿流程

### 第一步：Fork 并创建分支

1. 点击右上角 **Fork**，将本仓库 Fork 到你自己的 GitHub 账号下。
2. Clone 到本地：
   ```bash
   git clone https://github.com/<你的用户名>/EMU-Stu-Blog.git
   cd EMU-Stu-Blog
   ```
3. 基于 `main` 分支创建新分支，分支名建议用文章 slug：
   ```bash
   git checkout -b blog/my-article-name
   ```

### 第二步：写文章

在 `articles/` 目录下新建一个 Markdown 文件，**文件名即该文章的 URL slug**（即 `/article?slug=<文件名>`）。

**文件名规范（必须遵守）：**
- 只使用 **小写字母**、**数字** 和 **连字符（`-`）**
- 禁止使用中文、Emoji、空格或其他特殊字符
- 示例：`my-first-article.md` ✅ &emsp; `我的第一篇文章.md` ❌

**文章格式（`articles/my-article.md`）：**

```markdown
---
title: 文章标题（可选，不写则自动取正文的一阶标题）
excerpt: 文章摘要，展示在博客列表页，建议不超过 150 字（可选）
category: 文章分类，例如 "AI应用"、"前端技术"、"系统开发" 等（可选）
author: 你的名字
date: 2026-06-06
---

# 文章标题

正文内容……
```

> **提示：** frontmatter 中所有字段均为可选。如果不写 `title`，系统会自动取正文第一个 `#` 标题；不写 `date` 则默认为当天。

### 第三步：添加图片（如有）

将图片文件放入 `articles/images/` 目录，在 Markdown 中使用**相对路径**引用：

```markdown
![示意图](./images/my-screenshot.png)
```

**图片规范：**
- 文件名同样只使用小写字母、数字和连字符，避免中文或空格
- 建议压缩图片（推荐 WebP 或压缩后的 PNG/JPG），单张不超过 **2 MB**
- 所有文章的图片共享 `images/` 目录，请确保文件名不与已有图片冲突

### 第四步：提交 Pull Request

1. 提交你的改动并推送到你 Fork 的仓库：
   ```bash
   git add articles/
   git commit -m "docs: add article <your-article-slug>"
   git push origin blog/my-article-name
   ```

2. 打开本仓库，GitHub 会提示你创建 Pull Request，点击 **Compare & pull request**。

3. PR 标题建议格式：`[投稿] 你的文章标题`

4. 在 PR 描述中简单说明文章内容，方便维护者快速了解。

5. 等待维护者 Review 并合并。合并后 GitHub Action 会自动触发主站重新构建，**约 1~3 分钟**后即可在 [EMU-Stu 官网博客](https://emu-stu.github.io/blog) 看到你的文章。

## 注意事项

- 请确保 Markdown 格式正确，可在本地用任意 Markdown 预览工具检查
- 正文中的外部链接请使用完整 URL（`https://...`），图片请统一放 `images/` 目录，不要引用外部图床
- 如有疑问，可以在 PR 评论或 Issue 中留言

## 本地预览（可选）

如果你想在本地实时预览文章效果，可以按照 [EMU-Stu-Site](https://github.com/EMU-Stu/EMU-Stu-Site) 的说明启动本地开发服务器，它会自动拉取本仓库最新内容进行渲染。
