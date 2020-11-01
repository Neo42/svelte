---
title: <svelte:window>
---

就像你可以给任何 DOM 元素添加事件监听器一样，你也可以用 `<svelte:window>` 给 `window` 对象添加事件监听器。

在第33行，添加`keydown`监听器。

```html
<svelte:window on:keydown={handleKeydown}/>
```

> 和 DOM 元素一样，你也可以添加[事件修饰符](tutorial/event-modifiers)，比如 `preventDefault`。
