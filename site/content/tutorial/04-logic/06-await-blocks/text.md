---
title: await 代码块
---

大多数 Web 应用程序都必须在某些时候处理异步数据。Svelte 可以让你在标记中直接 _等待_ [promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises) 的值。

```html
{#await promise}
	<p>...waiting</p>
{:then number}
	<p>The number is {number}</p>
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}
```

Svelte 只会处理最新的 promise，也就是说，你不用担心多个 promise 出现冲突。

If you know that your promise can't reject, you can omit the `catch` block. You can also omit the first block if you don't want to show anything until the promise resolves:

如果你知道你的 promise 不可能出现拒绝，你就可以把 `catch` 代码块省略掉。如果你不想在 promise 决议之前显示任何东西，你也可以省略第一个代码块。

```html
{#await promise then value}
  <p>the value is {value}</p>
{/await}
```
