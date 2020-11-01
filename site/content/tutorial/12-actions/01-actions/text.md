---
title: use 指令
---

action 其实就是元素级的生命周期功能。它们对于这些东西很有用：

* 与第三方库进行交互
* 图片的懒加载
* 工具提示
* 添加自定义事件处理程序

在这个应用程序中，我们想让橙色的盒子"pannable"(可以平移)。它有 `panstart` 、`panmove` 和 `panend` 事件的处理程序，但这些不是原生的 DOM 事件。我们必须自己分发它们。首先，导入 `pannable` 函数...

```js
import { pannable } from './pannable.js';
```

......然后把它跟元素一起使用。

```html
<div class="box"
	use:pannable
	on:panstart={handlePanStart}
	on:panmove={handlePanMove}
	on:panend={handlePanEnd}
	style="transform:
		translate({$coords.x}px,{$coords.y}px)
		rotate({$coords.x * 0.2}deg)"
></div>
```

打开 `pannable.js` 文件。像过渡函数一样，action 函数接收一个 `node` 和一些可选的参数，并返回一个 action 对象。这个对象可以有一个 `destroy` 函数，当元素被解除挂载时，这个函数会被调用。

我们希望当用户在元素内按下鼠标按键时触发 `panstart` 事件，当用户拖动元素时触发 `panmove` 事件（`dx` 和 `dy` 属性会显示鼠标移动的距离），当用户向上抬起鼠标按键时触发 "panend "事件。一种实现可能是这样的。

```js
export function pannable(node) {
	let x;
	let y;

	function handleMousedown(event) {
		x = event.clientX;
		y = event.clientY;

		node.dispatchEvent(new CustomEvent('panstart', {
			detail: { x, y }
		}));

		window.addEventListener('mousemove', handleMousemove);
		window.addEventListener('mouseup', handleMouseup);
	}

	function handleMousemove(event) {
		const dx = event.clientX - x;
		const dy = event.clientY - y;
		x = event.clientX;
		y = event.clientY;

		node.dispatchEvent(new CustomEvent('panmove', {
			detail: { x, y, dx, dy }
		}));
	}

	function handleMouseup(event) {
		x = event.clientX;
		y = event.clientY;

		node.dispatchEvent(new CustomEvent('panend', {
			detail: { x, y }
		}));

		window.removeEventListener('mousemove', handleMousemove);
		window.removeEventListener('mouseup', handleMouseup);
	}

	node.addEventListener('mousedown', handleMousedown);

	return {
		destroy() {
			node.removeEventListener('mousedown', handleMousedown);
		}
	};
}
```

修改 `pannable` 函数，然后试着移动盒子。

> 这个实现只是为了演示目的--一个更完整的实现还应该考虑触屏事件。
