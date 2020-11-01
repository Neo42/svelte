---
title: 自定义 store
---

只要一个对象正确地实现了 `subscribe` 方法，那么它就是一个 store 。如果做到了这一点，其他的想怎么样都可以。因此，我们很容易创建具有特定领域逻辑的自定义 store 。

例如，我们前面的例子中的 `count` 存储可以含有 `increment` 、`decrement` 和 `reset` 方法，并没有使用 `set` 和 `update`。

```js
function createCount() {
	const { subscribe, set, update } = writable(0);

	return {
		subscribe,
		increment: () => update(n => n + 1),
		decrement: () => update(n => n - 1),
		reset: () => set(0)
	};
}
```

