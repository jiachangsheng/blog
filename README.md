# Blog

一个简洁的个人博客，基于 Astro 构建，采用科幻 AI 主题风格。

## 技术栈

- **框架**: Astro
- **内容**: MDX
- **主题**: 自定义科幻风格（深色 + 霓虹色）

## 项目结构

```
blog/
├── src/
│   ├── layouts/
│   │   └── Base.astro        # 公共布局
│   └── pages/
│       ├── index.astro       # 首页
│       ├── about.astro        # 关于页
│       └── blog/
│           ├── index.astro    # 博客列表
│           └── [slug].astro  # 文章详情
├── public/                   # 静态资源
├── astro.config.mjs          # Astro 配置
└── package.json
```

## 启动命令

```bash
# 安装依赖
npm install

# 开发模式启动
npm start

# 构建生产版本
npm run build
```

## 访问

开发服务器启动后访问 http://localhost:4321

## 部署

项目已配置为静态站点，可部署到 Vercel、Netlify 或 GitHub Pages。

```bash
npm run build
```

构建产物在 `dist/` 目录。
