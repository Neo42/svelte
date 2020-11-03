---
title: 自动订阅
---

前面例子中的应用程序已经可以正常使用了，但还有一个细微的 bug --`unsubscribe` 函数从未被调用。如果组件被多次实例化和销毁，这个 bug 将会导致 _内存泄漏_。

解决这个问题的方法之一是使用`onDestroy`[生命周期钩子](tutorial/ondestroy)。

```html
<script>
	import { onDestroy } from 'svelte';
	import { count } from './stores.js';
	import Incrementer from './Incrementer.svelte';
	import Decrementer from './Decrementer.svelte';
	import Resetter from './Resetter.svelte';

	let count_value;

	const unsubscribe = count.subscribe(value => {
		count_value = value;
	});

	onDestroy(unsubscribe);
</script>

<h1>The count is {count_value}</h1>
```

但这样会开始变得有点儿像模板代码，尤其是当你的组件订阅了多个 Store 时。与其用这个方法，Svelte有一个小技巧--你可以通过在 Store 名称前加上`$`来引用一个 Store 的值。

```html
<script>
	import { count } from './stores.js';
	import Incrementer from './Incrementer.svelte';
	import Decrementer from './Decrementer.svelte';
	import Resetter from './Resetter.svelte';
</script>

<h1>The count is {$count}</h1>
```

> 自动订阅只适用于在组件顶层作用域声明（或导入）的 Store 变量。

你也不仅可以在标记中使用 `$count` ，还可以在 `<script>` 中的任何地方使用它，比如在事件处理程序或响应式声明中。

> 任何以 `$` 开头的名字都被认为是在引用一个 Store 值。（在 Svelte 中）它实际上被用作一个保留字符--Svelte会阻止你用 `$` 前缀来声明自己的变量。