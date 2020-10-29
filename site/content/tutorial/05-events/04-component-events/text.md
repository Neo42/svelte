---
title: 组件事件
---

组件还可以分发事件。要做到这一点，它们必须创建一个事件分发器。修改 `Inner.svelte`：

```html
<script>
	import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();

	function sayHello() {
		dispatch('message', {
			text: 'Hello!'
		});
	}
</script>
```

> `createEventDispatcher`必须在组件第一次实例化时被调用--你不能这之后才调用它，比如放在 `setTimeout` 回调里。这样的话 `dispatch` 会被和组件实例相链接。