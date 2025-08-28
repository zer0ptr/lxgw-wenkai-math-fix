# 霞鹜文楷字体数学公式显示修复

## 问题描述

在使用霞鹜文楷字体（LXGW WenKai）的博客中，数学公式（通过 MathJax 或 KaTeX 渲染）会出现字体显示过小的问题。这是因为数学渲染库会重置或覆盖字体大小设置，导致数学公式的显示效果不佳。

## 解决方案

本项目提供了三个 CSS 修复文件来解决这个问题：

1. **`lxgw-wenkai-math-fix.css`** - 通用修复文件，适用于大多数情况
2. **`mathjax-fix.css`** - 专门针对 MathJax 的修复
3. **`katex-fix.css`** - 专门针对 KaTeX 的修复

## 使用方法

### 方法一：使用通用修复文件（推荐）

1. 下载 `lxgw-wenkai-math-fix.css` 文件
2. 将文件放置到你的 Hexo 博客的 `source/css/` 目录下
3. 在你的主题配置中引入这个 CSS 文件

#### 在 Hexo 主题中引入

**方法 A：修改主题的 head 模板**

在你的主题的 `layout/_partial/head.ejs`（或相应的模板文件）中添加：

```html
<!-- 霞鹜文楷数学公式修复 -->
<link rel="stylesheet" href="<%- url_for('/css/lxgw-wenkai-math-fix.css') %>">
```

**方法 B：通过主题配置文件**

如果你的主题支持自定义 CSS，可以在主题的 `_config.yml` 中添加：

```yaml
# 自定义 CSS
custom_css:
  - /css/lxgw-wenkai-math-fix.css
```

**方法 C：直接在文章中引入**

在需要修复的文章的 Front Matter 中添加：

```yaml
---
title: 你的文章标题
date: 2024-01-01
stylesheets:
  - /css/lxgw-wenkai-math-fix.css
---
```

### 方法二：使用专门的修复文件

如果你知道你的博客使用的是 MathJax 或 KaTeX，可以使用对应的专门修复文件：

- 对于 MathJax：使用 `mathjax-fix.css`
- 对于 KaTeX：使用 `katex-fix.css`

使用方法与通用修复文件相同。

### 方法三：CDN 引入（如果文件已上传到 CDN）

```html
<link rel="stylesheet" href="https://your-cdn-url/lxgw-wenkai-math-fix.css">
```

## 效果对比

### 修复前
- 数学公式字体过小，与正文字体大小不协调
- 行内公式可能出现垂直对齐问题
- 块级公式显示不够清晰

### 修复后
- 数学公式字体大小适中，与正文协调
- 行内公式垂直对齐正确
- 块级公式清晰易读
- 响应式设计，在移动设备上也有良好表现

## 技术细节

### 修复原理

1. **字体大小调整**：将数学公式的字体大小从默认值调整为 1.15em（行内）和 1.2em（块级）
2. **行高优化**：设置合适的行高以确保公式的可读性
3. **垂直对齐**：修复行内公式的垂直对齐问题
4. **响应式支持**：在不同屏幕尺寸下提供最佳显示效果

### 兼容性

- ✅ MathJax v2
- ✅ MathJax v3
- ✅ KaTeX
- ✅ 原生 MathML
- ✅ 移动设备
- ✅ 高分辨率屏幕

## 自定义调整

如果默认的字体大小不符合你的需求，可以修改 CSS 文件中的以下值：

```css
/* 行内公式字体大小 */
.math-inline {
    font-size: 1.05em !important; /* 可调整此值 */
}

/* 块级公式字体大小 */
.math-display {
    font-size: 1.2em !important; /* 可调整此值 */
}
```

## 常见问题

### Q: 修复后公式还是很小怎么办？
A: 检查是否有其他 CSS 规则覆盖了修复样式。可以尝试增加 CSS 选择器的优先级或调整字体大小值。

### Q: 修复后正文字体受到影响怎么办？
A: 本修复只针对数学公式元素，不应该影响正文。如果出现问题，请检查 CSS 选择器是否过于宽泛。

### Q: 在移动设备上效果不好怎么办？
A: 修复文件包含了响应式设计，如果效果不佳，可以调整媒体查询中的字体大小值。

### Q: 如何确定我的博客使用的是 MathJax 还是 KaTeX？
A: 查看页面源代码，搜索 "mathjax" 或 "katex" 关键词，或者使用浏览器开发者工具检查数学公式的 HTML 结构。

## 贡献

如果你发现问题或有改进建议，欢迎提交 Issue 或 Pull Request。

## 许可证

本项目采用 MIT 许可证。

## 相关链接

- [霞鹜文楷字体](https://github.com/lxgw/LxgwWenKai)
- [MathJax](https://www.mathjax.org/)
- [KaTeX](https://katex.org/)
- [Hexo](https://hexo.io/)