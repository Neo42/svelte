---
title: 带键的 each 代码块
---

在默认情况下，当你修改一个 `each` 块的值时，它将在该块的 _结尾_ 添加和删除项目，并更新所有已经改变的值。你可能不会想得到这样的效果。

至于为什么会这样，直接展示给你看会比用语言解释更容易一些。点击几次 `Remove first thing` 按钮，注意它正在从末尾删除 `<Thing>` 组件，并为余下的那些组件更新 `color`。而我们想删除第一个 `<Thing>` 组件，让其他组件不受影响。

为此，我们为 `each` 代码块指定一个唯一的标识符。

```html
{#each things as thing (thing.id)}
	<Thing current="{thing.color}" />
{/each}
```

> `(that.id)` 会告诉 Svelte 找出哪些东西发生了改变的方法。

> 你可以把任何对象作为键使用，因为 Svelte 内部使用了一个 `Map` -- 换句话说，你可以用 `(thing)` 代替 `(thing.id)`。然而，使用字符串或数字通常更安全一些，因为这样会使得键的身份在比如从 API 服务器更新新数据的情况下保持不变，不必担心出现相同的引用。
