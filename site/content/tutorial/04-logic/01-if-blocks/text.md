---
title: if 代码块
---

HTML 并没有一种方式来表达条件和循环之类的 _逻辑_ 。不过 Svelte 有。

为了有条件地渲染一些标记，我们用一个 `if` 代码块把它包装起来。

```html
{#if user.loggedIn}
	<button on:click="{toggle}">Log out</button>
{/if} {#if !user.loggedIn}
	<button on:click="{toggle}">Log in</button>
{/if}
```

试试看吧 - 修改一下组件，然后点击按钮。
