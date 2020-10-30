---
title: tick
---

`tick` 函数不同于其他生命周期函数，因为你可以在任何时候调用它，而不仅仅是在组件第一次初始化时。它会返回一个 promise，一旦有待定（pending）的状态变化被应用到DOM中，这个 promise 会马上决议（resolve）（或者如果没有待定的状态变化，则立即决议）。

当你在Svelte中更新组件状态时，它不会立即更新 DOM 。相反，它会等到下一个 _微任务_ ，看看有没有其他变化需要被应用，这其中也包括其他组件的变化。这样做可以避免不必要的工作，并允许浏览器更有效地批量处理任务。

你可以在这个例子中看到这个动作。选择一部分文本，并按下tab键。因为 `<textarea>` 的值发生了变化，当前的选择被清除了，光标讨厌地跳转到了最后。要解决这个问题，我们可以导入 `tick` ：

```js
import { tick } from 'svelte';
```

...并于我们在 `handleKeydown` 结尾设置 `this.selectionStart` 和 `this.selectionEnd` 之前立即运行它：

```js
await tick();
this.selectionStart = selectionStart;
this.selectionEnd = selectionEnd;
```