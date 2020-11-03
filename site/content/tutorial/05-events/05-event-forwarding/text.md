---
title: 事件转发
---

与 DOM 事件不同，组件事件并不会 _冒泡_ 。如果你想要监听的某个事件是绑定在一些嵌套得很深的组件上的，这个事件必须要经过中间那些的组件的 _转发_ 。

这里我们还保留着前一章节中的 `App.svelte` 和 `Inner.svelte`，但现在我们又加了一个包含着 `<Inner/>` 的 `Outer.svelte` 组件。

我们要想解决这个问题，有一种方法是在 `Outer.svelte` 中添加 `createEventDispatcher` ，监听 `message` 事件，并为其创建一个处理程序。

```html
<script>
	import Inner from './Inner.svelte';
	import { createEventDispatcher } from 'svelte';

	const dispatch = createEventDispatcher();

	function forward(event) {
		dispatch('message', event.detail);
	}
</script>

<Inner on:message={forward}/>
```

但这需要写很多代码，所以 Svelte 给了我们一个效果相同的简写 -- 一个没有值的 `on:message` 事件指令意味着 “转发所有的 `message` 事件”。

```html
<script>
	import Inner from './Inner.svelte';
</script>

<Inner on:message/>
```