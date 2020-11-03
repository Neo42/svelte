---
title: each 代码块绑定
---

你甚至可以在 `each` 代码块中为元素属性做绑定。

```html
<input
	type=checkbox
	bind:checked={todo.done}
>

<input
	placeholder="What needs to be done?"
	bind:value={todo.text}
>
```

> 请注意，与这些 <input> 元素进行交互将使数组发生改变。如果你喜欢使用不可变的数据，则应避免使用这些绑定，而应使用事件处理程序。