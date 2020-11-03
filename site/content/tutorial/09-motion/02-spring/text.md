---
title: spring
---

`spring`（弹簧） 函数是 `tweened` 的替代方案，通常对经常变化的值有更好的效果。

在这个例子中，我们有两个 Store --一个代表圆的坐标，一个代表圆的大小。让我们将它们转换为弹簧。

```html
<script>
	import { spring } from 'svelte/motion';

	let coords = spring({ x: 50, y: 50 });
	let size = spring(10);
</script>
```

两个弹簧都有默认的 `stiffness`（刚度） 和 `damping`（阻尼） 值，用于控制弹簧的...弹性。我们可以指定自己的初始值：

```js
let coords = spring({ x: 50, y: 50 }, {
	stiffness: 0.1,
	damping: 0.25
});
```

晃动你的鼠标，并尝试拖动滑块来感受它们怎样影响弹簧的行为。注意，你可以在弹簧还在运动的时候调整数值。