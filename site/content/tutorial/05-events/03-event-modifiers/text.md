---
title: Event modifiers
---

我们可以用 _修改器_ 来改变 DOM 事件处理程序的行为。例如，一个带有 `once` 修饰符的处理程序将会只运行一次。

```html
<script>
	function handleClick() {
		alert('no more alerts')
	}
</script>

<button on:click|once={handleClick}>
	Click me
</button>
```

修饰符的完整列表：

* `preventDefault`-在运行处理程序之前调用`event.preventDefault()`。例如，对客户端的表单处理很有用。
* `stopPropagation`-调用`event.stopPropagation()`，防止事件到达下一个元素。
* "被动" -- -- 提高触摸/轮子事件的滚动性能（Svelte将在安全的情况下自动添加）。
* "nonpassive" -- -- 明确设置 "passive: false"。
* `capture` -- -- 在*capture*阶段而不是*bubbling*阶段启动处理程序([MDN docs](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events#Event_bubbling_and_capture))
* "once" -- -- 在第一次运行后删除处理程序。
* `self`----只有当event.target是元素本身时才触发处理程序。

您可以将修饰符连锁使用，例如`on:click|once|capture={...}`。