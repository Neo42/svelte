---
title: 过渡事件
---

知道过渡何时即将开始和即将结束会对我们很有用。Svelte 可以像分发其他 DOM 事件一样分发过渡事件。

```html
<p
	transition:fly="{{ y: 200, duration: 2000 }}"
	on:introstart="{() => status = 'intro started'}"
	on:outrostart="{() => status = 'outro started'}"
	on:introend="{() => status = 'intro ended'}"
	on:outroend="{() => status = 'outro ended'}"
>
	Flies in and out
</p>
```