---
title: 赋值
---

Svelte 的核心是一个强大的 _响应式_ 系统，用于让 DOM 与应用程序状态保持同步--比如在对一个事件作出响应时。

为了做个演示，我们首先需要连接一个事件处理程序。将第 9 行替换成这样：

```html
<button on:click="{handleClick}"></button>
```

在 `handleClick` 函数里，我们只需要改变 `count` 的值就可以了。

```js
function handleClick() {
	count += 1;
}
```

Svelte 会用一些代码来 "检测" 这个赋值，这些代码会告诉 Svelte DOM 需要更新。
