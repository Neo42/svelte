---
title: DOM 事件
---

正如我们简要地了解过的，你可以使用 `on:` 指令来监听元素上的事件：

```html
<div on:mousemove={handleMousemove}>
	The mouse position is {m.x} x {m.y}
</div>
```