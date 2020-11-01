---
title: <svelte:body>
---

与`<svelte:window>`类似，`<svelte:body>` 元素可以让你监听在 `document.body` 上触发的事件。这对于 `mouseenter` 和 `mouseleave` 事件非常有用，因为这些事件不会在 `window` 上触发。

将 `mouseenter` 和 `mouseleave` 处理程序添加到 `<svelte:body>` 标签中。

```html
<svelte:body
	on:mouseenter={handleMouseenter}
	on:mouseleave={handleMouseleave}
/>
```