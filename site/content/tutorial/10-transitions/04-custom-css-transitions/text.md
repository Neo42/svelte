---
title: 自定义 CSS 过渡
---

`svelte/transition` 模块内置了一些的过渡，不过如果要创建自己的转场也很容易。例如，这是 `fade` 过渡的源代码。

```js
function fade(node, {
	delay = 0,
	duration = 400
}) {
	const o = +getComputedStyle(node).opacity;

	return {
		delay,
		duration,
		css: t => `opacity: ${t * o}`
	};
}
```

该函数接收两个参数——应用过渡的节点和一个被传进来的任意参数——并返回一个过渡对象，该对象可以具有以下属性。

* `delay` —— 过渡开始前要延迟多少毫秒。
* `duration` —— 过渡的时长，以毫秒为单位。
* `easing` —— 一个 `p => t` 缓动函数（见[制作 tweening](tutorial/tweened)）
* `css` —— `(t, u) => css` 函数，其中`u === 1 - t`。
* `tick` —— 一个 `(t, u) => {...}` 函数，对节点有一定影响。

`t`值在 intro 开始或 outro 结束时为`0`，在 intro 结束或 outro 开始时为`1`。

大多数情况下，你应该返回 `css` 属性，而 _不是_ `tick`属性，因为为了尽可能防止掉帧，CSS动画是在主线程之外运行的。Svelte会对过渡进行"模拟"并构建一个CSS动画，然后让它运行。

例如，`fade` 过渡会生成一个CSS动画，有点像这样：

```css
0% { opacity: 0 }
10% { opacity: 0.1 }
20% { opacity: 0.2 }
/* ... */
100% { opacity: 1 }
```

我们还可以玩得更花一点，搞点实在是莫名其妙的东西。

```html
<script>
	import { fade } from 'svelte/transition';
	import { elasticOut } from 'svelte/easing';

	let visible = true;

	function spin(node, { duration }) {
		return {
			duration,
			css: t => {
				const eased = elasticOut(t);

				return `
					transform: scale(${eased}) rotate(${eased * 1080}deg);
					color: hsl(
						${~~(t * 360)},
						${Math.min(100, 1000 - 1000 * t)}%,
						${Math.min(50, 500 - 500 * t)}%
					);`
			}
		};
	}
</script>
```

请记住：能力越大，责任越大。
