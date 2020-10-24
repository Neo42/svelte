---
title: each 代码块
---

如果你需要对数据列表进行循环，可以使用 `each` 代码块。

```html
<ul>
	{#each cats as cat}
	<li>
		<a target="_blank" href="https://www.youtube.com/watch?v={cat.id}">
			{cat.name}
		</a>
	</li>
	{/each}
</ul>
```

> 表达式(比如这个例子中的 `cats`)可以是任何数组或类似数组的对象(即它有一个 `length` 属性)。你可以用 `each [...iterable]` 来循环通用的 iterable。

你可以把当前的 _索引数_ 作为第二个参数，像这样。

```html
{#each cats as cat, i}
<li>
	<a target="_blank" href="https://www.youtube.com/watch?v={cat.id}">
		{i + 1}: {cat.name}
	</a>
</li>
{/each}
```

你可以按你的喜好使用解构 -- `each cats as { id, name }` --用 `id` 和 `name` 代替 `cat.id` 和 `cat.name`。
