---
title: contenteditable 绑定
---

带有 `contenteditable="true"` 属性的元素支持 `textContent` 和 `innerHTML` 绑定。

```html
<div
	contenteditable="true"
	bind:innerHTML={html}
></div>
```