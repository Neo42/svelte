---
title: DOM events
---

正如我们简单见过的，你可以使用 `on:` 指令监听元素上的事件：

```html
<div on:mousemove={handleMousemove}>
	The mouse position is {m.x} x {m.y}
</div>
```