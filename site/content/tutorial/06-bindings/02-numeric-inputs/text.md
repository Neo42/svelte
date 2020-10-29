---
title: 数值输入
---

在DOM中，一切都是字符串。这对你处理数值输入不太有帮助 -- `type="number"` 和 `type="range"`--这并没有什么帮助，因为这意味着你必须牢记在使用 `input.value` 之前强制把它转换为数值。

有了 `bind:value`，Svelte 就能帮你解决这个问题：

```html
<input type=number bind:value={a} min=0 max=10>
<input type=range bind:value={a} min=0 max=10>
```