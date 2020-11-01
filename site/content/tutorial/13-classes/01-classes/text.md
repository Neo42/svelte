---
title: 类指令
---

像其他元素属性一样，你可以用 JavaScript 元素属性来指定元素的类，见这里。

```html
<button
	class="{current === 'foo' ? 'selected' : ''}"
	on:click="{() => current = 'foo'}"
>foo</button>
```

这种模式在 UI 开发中太常见了，以至于 Svelte 专门有一个特殊的指令来简化它。

```html
<button
	class:selected="{current === 'foo'}"
	on:click="{() => current = 'foo'}"
>foo</button>
```

每当表达式的值是真值时，`selected`类就会被添加到元素中，当它是假值时，就会被删除。
