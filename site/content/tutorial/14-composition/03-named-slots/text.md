---
title: 命名插槽
---

前面的例子中包含了一个 *默认插槽* ，它显示的是一个组件的直系子组件。有时候，你需要对位置有更多的控制，比如这个 `<ContactCard>`。这种情况下，我们可以使用 _命名插槽_。

在`ContactCard.svelte`中，给每个槽添加一个`name`属性。

```html
<article class="contact-card">
	<h2>
		<slot name="name">
			<span class="missing">Unknown name</span>
		</slot>
	</h2>

	<div class="address">
		<slot name="address">
			<span class="missing">Unknown address</span>
		</slot>
	</div>

	<div class="email">
		<slot name="email">
			<span class="missing">Unknown email</span>
		</slot>
	</div>
</article>
```

然后，在 `<ContactCard>` 组件中添加带有相应的 `slot="..."` 属性的元素。

```html
<ContactCard>
	<span slot="name">
		P. Sherman
	</span>

	<span slot="address">
		42 Wallaby Way<br>
		Sydney
	</span>
</ContactCard>
```