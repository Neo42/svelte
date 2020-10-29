---
title: textarea 输入
---

`<textarea>` 元素的行为和 Svelte 中的文本输入差不多--使用 `bind:value`：

```html
<textarea bind:value={value}></textarea>
```

在类似的情况下，如果名字相符，我们也可以使用简写形式。

```html
<textarea bind:value></textarea>
```

这适用于所有的绑定，而不仅仅是文本区。