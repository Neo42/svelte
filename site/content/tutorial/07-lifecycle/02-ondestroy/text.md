---
title: onDestroy
---

如果你想在组件被销毁时运行代码，那么就使用 `onDestroy`。

比如说，我们可以在组件初始化时添加一个 `setInterval` 函数，并在不再需要它时把它清理掉。这样做可以防止内存泄漏。

```html
<script>
	import { onDestroy } from 'svelte';

	let seconds = 0;
	const interval = setInterval(() => seconds += 1, 1000);

	onDestroy(() => clearInterval(interval));
</script>
```

尽管在组件初始化期间调用生命周期函数很重要，但是在 _什么地方_ 调用它们并不重要。 因此，如果需要，我们可以将时间间隔的逻辑抽象到 `utils.js` 中的一个辅助函数中。

```js
import { onDestroy } from 'svelte';

export function onInterval(callback, milliseconds) {
	const interval = setInterval(callback, milliseconds);

	onDestroy(() => {
		clearInterval(interval);
	});
}
```

...并把它导入到我们的组件中：

```html
<script>
	import { onInterval } from './utils.js';

	let seconds = 0;
	onInterval(() => seconds += 1, 1000);
</script>
```