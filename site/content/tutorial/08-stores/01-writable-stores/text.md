---
title: 可写入 store 
---

并非所有应用程序状态都属于应用程序的组件层次结构之内。 有时，你会用到一些值，它们需要多个不相关的组件或常规的JavaScript模块都对其进行访问。

在Svelte中，我们用 _ store _ 来实现这一点。 store 就是一个带有 `subscribe` 方法的对象，它可以让有需要的各方在其存储的值发生改变时收到通知。在 `App.svelte` 中，`count` 就是一个store，而我们正在在往 `count.subscribe` 回调中设置`count_value`。

点击`stores.js`标签页，就可以看到`count`的定义。它是一个 _可写入_ 的 store ，这意味着除了`subscribe`之外，它还有 `set` 和 `update` 方法。

现在进入 `Incrementer.svelte` 选项卡，这样我们就可以给 `+` 按钮接线了。

```js
function increment() {
	count.update(n => n + 1);
}
```

点击`+`按钮，现在它应该可以更新计数了。对 "Decrementer.svelte "做相反的操作。

最后，在`Resetter.svelte`中，实现`reset`。

```js
function reset() {
	count.set(0);
}
```