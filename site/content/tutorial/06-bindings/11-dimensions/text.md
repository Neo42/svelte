---
title: 尺寸
---

每个块级元素都有 `clientWidth`、`clientHeight`、`offsetWidth` 和 `offsetHeight` 的绑定。

```html
<div bind:clientWidth={w} bind:clientHeight={h}>
	<span style="font-size: {size}px">{text}</span>
</div>
```

这些绑定是只读的 -- -- 改变 `w` 和 `h` 的值不会有任何影响。

> 元素的测量使用的是一种类似于[这个](http://www.backalleycoder.com/2013/03/18/cross-browser-event-based-element-resize-detection/)的技术。这会造成一些额外的性能开销，所以不建议在大量元素上使用这种方法。
>
> 带有 `display: inline` 样式的元素不能用这种方法测量；不能包含其他元素的元素（如`<canvas>`）也不能。在这种情况下，你就需要测量一个包装元素。