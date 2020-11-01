---
title: 添加参数
---

像过渡和动画一样，一个 action 可以接受一个参数，调用 action 函数时会把 action 所属的元素和这个参数一起使用。

在这里，我们使用了一个 `longpress` action ，只要用户在给定的时间内按住按钮，就会触发一个同名的事件。现在，如果你切换到 `longpress.js` 文件，你会发现它被写死成了 500ms。

我们可以改变 action 函数，接受一个 `duration` 作为第二个参数，并将这个 `duration` 传递给调用函数的 `setTimeout`。

```js
export function longpress(node, duration) {
	// ...

	const handleMousedown = () => {
		timer = setTimeout(() => {
			node.dispatchEvent(
				new CustomEvent('longpress')
			);
		}, duration);
	};

	// ...
}
```

回到 `App.svelte` 中，我们可以将 `duration` 值传给这个 action 。

```html
<button use:longpress={duration}
```

这样 _几乎_ 就是能行了——现在事件只有在2秒后才会启动。但如果你把时间长度降下来，它仍然需要两秒钟。

为了改变这种情况，我们可以在 `longpress.js` 中添加一个 `update` 方法。每当参数发生变化时，这个方法就会被调用。

```js
return {
	update(newDuration) {
		duration = newDuration;
	},
	// ...
};
```

> 如果你需要把多个参数传给一个 action ，请将它们组合成一个对象，比如 `use:longpress={{duration, spiciness}}`。