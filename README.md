## Description
My blog using the project [Mizuki](https://github.com/matsuzaka-yuki/Mizuki).

The usage document is [here](https://docs.mizuki.mysqil.com/).

Below I show some usage markdown part in case I forget how to use it.

## Commands

Here shows some basic command to use:

| Command                    | Action                                   |
|:---------------------------|:-----------------------------------------|
| `pnpm install`             | Install dependencies                     |
| `pnpm dev`                 | Start local dev server at `localhost:4321` |
| `pnpm build`               | Build production site to `./dist/`       |
| `pnpm preview`             | Preview build locally before deployment  |
| `pnpm check`               | Run Astro error checking                 |
| `pnpm format`              | Format code with Biome                   |
| `pnpm lint`                | Check and fix code issues                |
| `pnpm new-post <filename>` | Create a new blog post                   |
| `pnpm astro ...`           | Run Astro CLI commands                   |

upload method 

```
git add .
git commit -m "" (comment for the purpose of the renew)
git push origin main (I put the project in main branch)
```

## Basic Configuration

Edit `src/config.ts` to customize your blog:

```typescript
export const siteConfig: SiteConfig = {
  title: "Your Blog Name",
  subtitle: "Your Blog Description",
  lang: "en", // or "zh-CN", "ja", etc.
  themeColor: {
    hue: 210, // 0-360, theme hue
    fixed: false, // Hide theme color picker
  },
  banner: {
    enable: true,
    src: ["assets/banner/1.webp"], // Banner images
    carousel: {
      enable: true,
      interval: 0.8, // seconds
    },
  },
};
```

## Feature Page Configuration

- **Anime Page:** Edit anime list in `src/pages/anime.astro`
- **Friends Page:** Edit friend data in `src/content/spec/friends.md`
- **Diary Page:** Edit moments in `src/pages/diary.astro`
- **About Page:** Edit content in `src/content/spec/about.md`

## Frontmatter 字段说明

- **title**: 文章标题（必需）
- **published**: 发布日期（必需）
- **description**: 文章描述，用于 SEO 和预览
- **image**: 封面图片路径（相对于文章文件）
- **tags**: 标签数组，用于分类
- **category**: 文章分类
- **draft**: 设置为 `true` 在生产环境中隐藏文章
- **pinned**: 设置为 `true` 将文章置顶
- **lang**: 文章语言（仅当与站点默认语言不同时设置）

## 置顶文章功能

`pinned` 字段允许您将重要文章置顶到博客列表的顶部。置顶文章将始终显示在普通文章之前，无论其发布日期如何。

**使用方法：**
```yaml
pinned: true  # 将此文章置顶
pinned: false # 普通文章（默认）
```

**排序规则：**
1. 置顶文章优先显示，按发布日期排序（最新在前）
2. 普通文章随后显示，按发布日期排序（最新在前）

## 🧩 Markdown 扩展语法

Mizuki 支持超越标准 GitHub Flavored Markdown 的增强功能：

### 📝 增强写作
- **提示框：** 使用 `> [!NOTE]`、`> [!TIP]`、`> [!WARNING]` 等创建精美的标注框
- **数学公式：** 使用 `$行内$` 和 `$$块级$$` 语法编写 LaTeX 数学公式
- **代码高亮：** 高级语法高亮，支持行号和复制按钮
- **GitHub 卡片：** 使用 `::github{repo="用户/仓库"}` 嵌入仓库卡片

### 🎨 视觉元素
- **图片画廊：** 自动 PhotoSwipe 集成，支持图片查看
- **可折叠部分：** 创建可展开的内容块
- **自定义组件：** 使用特殊指令增强内容

### 📊 内容组织
- **目录：** 从标题自动生成，支持平滑滚动
- **阅读时间：** 自动计算和显示
- **文章元数据：** 丰富的前言支持，包含分类和标签

