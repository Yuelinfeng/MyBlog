---
layout: ../../layouts/MarkdownPostLayout.astro
title: "了解 Astro 中的 Markdown"
author: Astro 学习者
pubDate: 2022-08-08
tags: ["astro", "learning"]
---
今天我收获颇丰！Astro 支持使用 Markdown 来创作，同时还可以使用来自 frontmatter 中的变量。我甚至能在 Astro 布局组件中拿到这些变量。

## 批量获取所有文章数据:
`const myPosts = Object.values(import.meta.glob('./posts/*.md', { eager: true }));`\
_一次性导入 ./posts/ 文件夹下所有 .md（Markdown）文件，并把它们的内容收集到一个数组中，方便后续统一处理。_

- `import.meta.glob('./posts/*.md', { eager: true })`\
这是 Astro/Vite 提供的一个 API，用于**批量导入匹配路径的文件**。
  - './posts/*.md'：匹配 posts 文件夹下所有 .md 文件。
  - { eager: true }：表示立即导入所有文件（不是懒加载），这样可以直接访问文件内容和元数据。
- `Object.values(...)` \
因为 import.meta.glob 返回的是一个对象（key 是文件路径，value 是文件内容），用 Object.values 把所有 value（即每个 Markdown 文件的内容）取出来，组成一个数组。
- `const myPosts = ...`\
最终，myPosts 就是一个数组，里面每一项都是一个 Markdown 文件的内容和 frontmatter 信息。