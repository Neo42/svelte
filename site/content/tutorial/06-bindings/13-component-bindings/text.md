---
title: 组件绑定
---

与你可以绑定 DOM 元素的属性类似，你也可以对组件的 prop 做绑定。例如，我们可以像绑定一个表单元素一样对这个 `<Keypad>` 组件的 `value` prop 做绑定。

```html
<Keypad bind:value={pin} on:submit={handleSubmit}/>
```

现在，当用户与 Keypad 交互时，父组件中的 `pin` 值将立即更新。

> 尽量少用组件绑定。如果你用的组件绑定太多，就很难跟踪应用程序中的数据流，特别是在没有"唯一真理之源"的情况下。