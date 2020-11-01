---
title: 可读取 store 
---

并不是所有的 store 都可以被一个对其持有引用的东西进行写入。比如，你可能有一个代表鼠标位置或用户地理位置的 store ，而谁都不应该有能力从'外部'设置这些值。对于这种情况，我们使用 _可读取_ 的 store 。

点击到 "stores.js “标签页。 `readable` 的第一个参数是一个初始值，如果你还没有初始值，可以把它设置成 `null` 或 `undefined` 。第二个参数是一个 `start` 函数，它接受一个 `set` 回调并返回一个 `stop` 函数。当 store 得到第一个订阅者时会调用`start`函数；当最后一个订阅者取消订阅时会调用 `stop` 函数。

```js
export const time = readable(new Date(), function start(set) {
	const interval = setInterval(() => {
		set(new Date());
	}, 1000);

	return function stop() {
		clearInterval(interval);
	};
});
```
