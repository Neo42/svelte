---
title: this
---

只读的 `this` 绑定适用于所有元素（和组件），让你拿到一个对于已经显示出来的元素的引用。例如，我们可以拿到对`<canvas>` 元素的引用。

```html
<canvas
	bind:this={canvas}
	width={32}
	height={32}
></canvas>
```

注意在组件挂载之前，`canvas` 的值将是 `undefined`，所以我们将逻辑放在 `onMount` [生命周期函数](tutorial/onmount)中。