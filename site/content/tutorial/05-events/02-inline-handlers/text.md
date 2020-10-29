---
title: 行内处理程序
---

你也可以在行内声明事件处理程序。

```html
<div on:mousemove="{e => m = { x: e.clientX, y: e.clientY }}">
	The mouse position is {m.x} x {m.y}
</div>
```

其中的引号是可以省略的，但在某些环境中它们会对语法高亮有帮助。

> 一些框架可能会建议你因为性能而避免使用行内事件处理程序，特别是在循环中。这个建议并不适用于 Svelte --无论你选择哪种形式，编译器都会一直做正确的事。