---
title: 分组输入
---

如果你有多个输入都与同一个值有关，你可以使用 `bind:group` 和 `value` 属性。同一组中的单选框输入是互斥的；同一组中的复选框输入会形成一个被选中值的数组。

为每个输入添加 `bind:group`。

```html
<input type=radio bind:group={scoops} value={1}>
```

在这个例子中，我们可以通过将复选框的输入移到 `each` 代码块中来简化代码。首先，在 `<script>` 代码块中添加一个 `menu` 变量。

```js
let menu = [
	'Cookies and cream',
	'Mint choc chip',
	'Raspberry ripple'
];
```

...然后替换第二部分。

```html
<h2>Flavours</h2>

{#each menu as flavour}
	<label>
		<input type=checkbox bind:group={flavours} value={flavour}>
		{flavour}
	</label>
{/each}
```

现在要把我们的冰淇淋菜单扩展成令人怦然心动的新模样就很容易了。