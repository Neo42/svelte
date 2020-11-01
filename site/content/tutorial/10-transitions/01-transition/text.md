---
title: transition 指令
---

通过优雅地将元素移入和移出DOM，我们可以使用户界面更具吸引力。 Svelte通过 `transition`（过渡） 指令使此操作非常容易。

首先，从 `svelte/transition` 中导入 `fade` 函数...。

```html
<script>
	import { fade } from 'svelte/transition';
	let visible = true;
</script>
```

...然后把它添加到 `<p>` 元素中：

```html
<p transition:fade>Fades in and out</p>
```