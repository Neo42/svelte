---
title: 样式
---

就像在 HTML 中一样，你可以在组件中添加一个 `<style>` 标签。 让我们给 `<p>` 元素添加一些样式：

```html
<style>
	p {
		color: purple;
		font-family: "Comic Sans MS", cursive;
		font-size: 2em;
	}
</style>

<p>This is a paragraph.</p>
```

重要的是，这些规则仅在 _当前组件范围内_ 起作用。 你不会意外更改你应用程序中其他地方 `<p>` 元素的样式，正如我们将在下一步中看到的那样。
