---
title: 复选框输入
---

复选框是用来在状态之间切换的。我们并不绑定 `input.value`，而是绑定 `input.checked`。

```html
<input type=checkbox bind:checked={yes}>
```