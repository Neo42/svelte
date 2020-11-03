---
title: 插槽后备
---

一个组件可以通过在 `<slot>` 元素中放入内容，为任何空着的插槽指定 _后备内容_ 。

```html
<div class="box">
	<slot>
		<em>no content was provided</em>
	</slot>
</div>
```

现在我们可以在没有任何子组件的情况下创建 `<Box>` 的实例。

```html
<Box>
	<h2>Hello!</h2>
	<p>This is a box. It can contain anything.</p>
</Box>

<Box/>
```
