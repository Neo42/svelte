---
title: 插槽 props
---

在这个应用中，我们有一个 `<Hoverable>` 组件，它可以跟踪鼠标现在是不是悬浮它上面。它需要将这些数据 *回传* 给父组件，这样我们就可以更新插槽中的内容。

为此，我们使用 *插槽 props* 。在 `Hoverable.svelte` 中，将 `hovering` 值传入插槽中。

```html
<div on:mouseenter={enter} on:mouseleave={leave}>
	<slot hovering={hovering}></slot>
</div>
```

> 记住，如果你愿意，你也可以使用 `{hovering}` 简写。

然后，为了让 `hovering` 暴露在 `<Hoverable>` 组件的内容中，我们使用 `let` 指令。

```html
<Hoverable let:hovering={hovering}>
	<div class:active={hovering}>
		{#if hovering}
			<p>I am being hovered upon.</p>
		{:else}
			<p>Hover over me!</p>
		{/if}
	</div>
</Hoverable>
```

如果你愿意，你可以重命名这个变量 —— 我们在父组件中就把它称作 `active`。

```html
<Hoverable let:hovering={active}>
	<div class:active>
		{#if active}
			<p>I am being hovered upon.</p>
		{:else}
			<p>Hover over me!</p>
		{/if}
	</div>
</Hoverable>
```

这样的组件你想用多少都可以，而且插槽中的 props 的有效范围会一直保持在声明它们的组件内部。

> 命名的插槽也可以用 props；要在带有 `slot="..."` 属性的元素上使用 `let` 指令，而不是在组件本身上使用。