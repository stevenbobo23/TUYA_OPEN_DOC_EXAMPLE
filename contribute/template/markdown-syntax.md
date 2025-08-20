---
title: Markdown 语法快速指南
---

# Markdown 语法在 Docusaurus 文档中的使用

Docusaurus 支持使用 **Markdown** 作为主要的内容编写格式，并通过 MDX 编译器将 Markdown 文件转换为 React 组件。本文将介绍在 Docusaurus 中常用的 Markdown 语法及其用法。

## 1. 标题

使用 `#` 表示一级标题，`##` 表示二级标题，依此类推。

```markdown
# 一级标题
## 二级标题
### 三级标题
```

## 2. 强调

- **粗体**：`**粗体**` 或 `__粗体__`
- _斜体_：`*斜体*` 或 `_斜体_`

## 3. 链接与图片

- 链接：`[Docusaurus 官网](https://docusaurus.io/)`
- 图片：`![图片描述](/img/docusaurus.png)`

## 4. 代码块

使用三个反引号包裹代码，可以指定语言高亮：

````markdown
```js
console.log('Hello, Docusaurus!');
```
````
Demo:
```js
console.log('Hello, Docusaurus!');
```

## 5. 引用
使用 `>` 表示引用：


```markdown
> 这是一段引用内容。
```
Demo:
> 这是一段引用内容。


## 6. 详情（Details）

Docusaurus 支持嵌入 HTML 元素，如 `<details>`，并有美观的样式：

```markdown
<details>
  <summary>点击展开</summary>
  这里是详细内容，可以包含 **Markdown** 语法。
</details>
```
Demo:
<details>
  <summary>点击展开</summary>
  这里是详细内容，可以包含 **Markdown** 语法。
</details>



## 7. Front Matter（前言）

每个 Markdown 文件顶部可以添加元数据，使用三条短横线包裹，内容为 YAML 格式：

```markdown
---
title: 文档标题
description: 这是文档的描述
---
```

## 8. MDX 与 CommonMark

- Docusaurus v3 默认所有 `.md` 和 `.mdx` 文件都使用 MDX 解析器，支持在 Markdown 中直接嵌入 React 组件。
- 若需使用标准 CommonMark，可在 `docusaurus.config.js` 配置 `markdown.format: 'detect'`，`.md` 文件将用 CommonMark 解析，`.mdx` 用 MDX。
- 详情见[官方文档](https://docusaurus.io/zh-CN/docs/markdown-features#mdx-vs-commonmark)。

## 9. 告示

````markdown
:::note
内容
:::

# 其他可用
[note/tip/info/warning/danger]
````

:::note

Some **content** with _Markdown_ `syntax`. Check [this `api`](#).

:::

:::tip

Some **content** with _Markdown_ `syntax`. Check [this `api`](#).

:::

:::info

Some **content** with _Markdown_ `syntax`. Check [this `api`](#).

:::

:::warning

Some **content** with _Markdown_ `syntax`. Check [this `api`](#).

:::

:::danger

Some **content** with _Markdown_ `syntax`. Check [this `api`](#).

:::

## 10. Docusaurus 特有功能

- 支持[选项卡](https://docusaurus.io/zh-CN/docs/markdown-features#选项卡)、[告示](https://docusaurus.io/zh-CN/docs/markdown-features#告示)、[数学公式](https://docusaurus.io/zh-CN/docs/markdown-features#数学公式)等扩展语法。
- 可通过 MDX 直接在文档中插入 React 组件。


## 11. 参考资料

- [Docusaurus 官方 Markdown 特性文档](https://docusaurus.io/zh-CN/docs/markdown-features)

---

如需调试 MDX 语法，可使用 [MDX Playground](https://mdxjs.com/playground)。
