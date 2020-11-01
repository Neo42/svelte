---
title: 插槽
---

就像元素可以有子元素一样...

```html
<div>
	<p>I'm a child of the div</p>
</div>
```

...组件也可以有子组件。不过，在组件接受子组件之前，它需要知道应该把它们放在哪里。我们通过 `<slot>` （插槽）元素来实现。把它放在 `Box.svelte` 里面。

```html
<div class="box">
	<slot></slot>
</div>
```

你现在可以把东西放进盒子里了：

```html
<Box>
	<h2>Hello!</h2>
	<p>This is a box. It can contain anything.</p>
</Box>
```