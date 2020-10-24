---
title: else 代码块
---

由于 `if user.loggedIn` 和 `if !user.loggedIn` 这两个条件是互斥的，我们可以使用 `else` 代码块把这个组件稍微简化一下。

```html
{#if user.loggedIn}
	<button on:click="{toggle}">Log out</button>
{:else}
	<button on:click="{toggle}">Log in</button>
{/if}
```

> `#` 字符永远表示一个 _代码块起始_ 标签。`/` 字符永远表示一个 _代码块结束_ 标签。`:` 字符，比如 `{:else}`，表示一个 _代码块延续_ 标签。不用担心，你已经学会了 Svelte 添加到 HTML 中的几乎所有语法。
