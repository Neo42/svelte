---
title: 检查插槽内容
---

在某些情况下，你可能想根据父组件向某个插槽传入了内容与否来控制你组件的若干个部分。也许你在这个插槽外加了一层包装，如果这个插槽是空的，你就希望不渲染这层包装。或者也许你想只在插槽存在时添加一个类。你可以通过检查特殊变量 `$$slots` 的属性来实现。

`$$slots` 是一个对象，它的键是父组件传入的插槽的名称。如果父组件将一个插槽留空，那么`$$slots`将不会保留这个插槽的记录。

请注意，在这个例子中，两个 `<Project>` 实例都渲染了一个评论区和一个通知圆点——尽管只有一个里面有评论。我们要使用 `$$slots` 来确保只有当父组件 `<App>` 为 `comments` 插槽传入内容时，我们才渲染这些元素。

在 `Project.svelte` 中，更新 `<article>` 的 `class:has-discussion` 指令：

```html
<article class:has-discussion="{$$slots.comments}"></article>
```

接下来，把 `comments` 插槽及包装它的 `<div>` 放在一个检查 `$$slots` 的 `if` 代码块中：

```html
{#if $$slots.comments}
<div class="discussion">
  <h3>Comments</h3>
  <slot name="comments"></slot>
</div>
{/if}
```

现在，当 `<App>`中的 `comments` 插槽为空时，评论区和通知点将不会被渲染。
