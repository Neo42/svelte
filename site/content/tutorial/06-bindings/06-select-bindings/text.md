---
title: select 绑定
---

我们也可以将 `<select>` 元素来与 `bind:value` 搭配使用。修改第24行：

```html
<select bind:value={selected} on:change="{() => answer = ''}">
```

请注意，`<option>`值是对象而不是字符串。Svelte 并不会介意。

> 由于我们没有设置 `selected` 的初始值，绑定会自动把它设置为默认值（列表中的第一个）。但要注意--在绑定被初始化之前，`selected` 仍然是 undefined，所以我们不能在模板中盲目使用像 `selected.id` 之类的引用。