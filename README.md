# EMU-Stu-Blog

本仓库是 [EMU-Stu-Site](https://github.com/EMU-Stu/EMU-Stu-Site) 的**博客文章**内容仓库。

主站在构建时会自动 clone 本仓库到 `frontend/docs/`（由 `scripts/fetch-docs.mjs` 完成），Vite 通过 `import.meta.glob` 把所有文章打包进站点。

## 目录结构

```
.
├── articles/                       博客文章正文（Markdown）
│   ├── *.md                        文章 Markdown 文件，文件名即 URL slug
│   └── images/                     文章引用的图片资源
└── .github/workflows/
    └── notify-main-site.yml        push 后通知主仓库重新构建部署
```

## 写文章

1. Fork 本仓库到你的 GitHub 账号下，然后 Clone 到本地，切换到 `main` 分支，创建新分支 `blog/<blog-name>`。

2. 在 `articles/` 下新建 `<blog-name>.md`，文件名即 URL slug(`/article?slug=<blog-name>`)。

   文件名请用 **小写字母** 和 **连字符(`-`)** 组成，严禁使用 **中文字符**、**Emoji**、**空格** 等特殊字符，以免引起 URL 编码问题。

3. 顶部可选地写 YAML frontmatter:

   ```markdown
   ---
   excerpt: 文章摘要，建议不超过 150 字
   category: 文章分类，例如 "AI应用"、"前端技术" 等
   author: 你的名字
   date: 文章发布日期，例如 2026-06-06
   ---

   # 正文标题

   正文内容
   ...
   ```

4. 图片放 `articles/images/`,在 Markdown 中用相对路径引用,例如 `![示意图](./images/foo.png)`。

5. 完成后提交 PR 到本仓库 `main` 分支，PR 合并后会自动触发 GitHub Action 通知主站重新部署，过一会儿就能在 [EMU-Stu 官网](https://emu-stu.github.io/blog) 上看到你的文章了。

