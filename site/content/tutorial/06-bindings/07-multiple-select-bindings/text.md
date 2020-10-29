---
title: Select multiple
---

select可以使用 `multiple` 属性，这样的话，它将生成一个数组，而不是选择一个单一值。

回到我们的[前面的冰淇淋例子](tutorial/group-inputs)，我们可以用`<select multiple>`代替复选框。

```html
<h2>Flavours</h2>

<select multiple bind:value={flavours}>
	{#each menu as flavour}
		<option value={flavour}>
			{flavour}
		</option>
	{/each}
</select>
```