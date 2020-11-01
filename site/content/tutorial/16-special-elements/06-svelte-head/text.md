---
title: <svelte:head>
---

`<svelte:head>` 元素可以让你在文档的 `<head>` 中插入元素。

```html
<svelte:head>
	<link rel="stylesheet" href="tutorial/dark-theme.css">
</svelte:head>
```

> 在服务器端渲染(SSR)模式下，`<svelte:head>` 的内容会从 HTML 的其他部分分开返回。