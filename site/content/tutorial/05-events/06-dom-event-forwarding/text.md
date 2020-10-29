---
title: DOM 事件转发
---

事件转发也适用于DOM事件。

我们想在点击我们的 `<CustomButton>` 收到通知 -- 要做到这一点，我们只需要转发 `CustomButton.svelte` 中 `<button>` 元素上的 `click` 事件。

```html
<button on:click>
	Click me
</button>
```