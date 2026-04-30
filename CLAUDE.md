# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 项目概述

这是一个基于 Astro 框架的静态博客，采用科幻 AI 主题风格（深色 + 霓虹色）。项目使用 MDX 内容格式，支持标签、搜索、SEO 和评论功能。

## 开发命令

- 安装依赖：`npm install`
- 启动开发服务器：`npm start`（运行 `astro dev`，默认地址：http://localhost:4321）
- 生产构建：`npm run build`（输出静态站点到 `dist/`）

## 项目结构

```
blog/
├── src/
│   ├── content/
│   │   ├── blog/              # 博客文章 (MDX 格式)
│   │   └── config.ts          # 内容集合 schema 定义
│   ├── layouts/
│   │   └── Base.astro         # 公共布局（深色/霓虹风格、导航、SEO 元标签）
│   └── pages/
│       ├── index.astro        # 首页（展示最新 5 篇文章）
│       ├── about.astro        # 关于页
│       ├── search.astro       # 搜索页（客户端搜索）
│       ├── tags/[tag].astro   # 标签筛选页
│       └── blog/
│           ├── index.astro    # 博客列表页
│           └── [slug].astro   # 文章详情页
├── public/                    # 静态资源
├── astro.config.mjs           # Astro 配置
└── package.json
```

## 技术栈

- **框架**: Astro（静态站点生成器）
- **内容**: MDX（@astrojs/mdx）
- **SEO**: @astrojs/sitemap
- **搜索**: Fuse.js（客户端模糊搜索）

## 核心配置

### astro.config.mjs

```javascript
export default defineConfig({
  site: 'https://your-blog-url.com',  // 需要替换为实际 URL
  integrations: [mdx(), sitemap()],
});
```

### 内容 Schema (src/content/config.ts)

博客文章包含以下字段：
- `title` - 文章标题
- `description` - 文章描述
- `pubDate` - 发布日期
- `tags` - 标签数组

## 路由说明

| 路径 | 文件 | 说明 |
|------|------|------|
| `/` | `src/pages/index.astro` | 首页，最新 5 篇文章 |
| `/blog` | `src/pages/blog/index.astro` | 博客列表，全量文章 |
| `/blog/[slug]` | `src/pages/blog/[slug].astro` | 文章详情页 |
| `/tags/[tag]` | `src/pages/tags/[tag].astro` | 标签筛选页 |
| `/search` | `src/pages/search.astro` | 客户端搜索页 |

## 已知待完成配置

1. **`astro.config.mjs`** - `site` 字段使用占位符 `https://your-blog-url.com`，需替换为实际博客地址（用于 canonical URL 和 sitemap 生成）

2. **Giscus 评论系统** - `src/pages/blog/[slug].astro` 中的 Giscus 配置（`data-repo`、ID 等）为占位符，需替换为真实 GitHub 仓库信息才能启用评论功能

## 测试

项目中尚未配置测试框架和测试脚本。