---
title: onMount
---

每个组件都有一个 _生命周期_ ，这个周期从组件创建时开始，到组件销毁时结束。有一些函数可以让你在生命周期的关键时刻运行代码。

你最常使用的将会是`onMount`，它会在组件第一次被渲染到 DOM 中之后运行。[之前](tutorial/bind-this)我们在 `<canvas>` 元素被渲染之后需要与之交互时简单地了解过这个函数。

我们要添加一个 `onMount` 处理程序，用它通过网络加载一些数据。

```html
<script>
	import { onMount } from 'svelte';

	let photos = [];

	onMount(async () => {
		const res = await fetch(`https://jsonplaceholder.typicode.com/photos?_limit=20`);
		photos = await res.json();
	});
</script>
```

> 出于服务器端渲染（SSR）的考虑，一般推荐将 `fetch` 放在 `onMount` 中，而不是放在顶层的 `<script>` 中。除了 `onDestroy`，生命周期函数都不会在 SSR 期间运行，也就意味着我们可以不用在组件被挂载到 DOM 中之后再获取本来应该被惰性加载的数据。

生命周期函数必须在组件初始化时调用，以便回调与组件实例绑定--而不是（比如说）被写在 `setTimeout` 中。

如果 `onMount` 回调返回的是一个函数，那么这个被返回的函数将会在组件销毁时被调用。