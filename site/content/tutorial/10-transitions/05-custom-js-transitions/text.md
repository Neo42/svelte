---
title: 自定义 JS 过渡
---

尽管一般来说，你应该尽可能地使用CSS来实现过渡，但有些效果如果不用JavaScript是无法实现的，比如打字机效果。

```js
function typewriter(node, { speed = 50 }) {
	const valid = (
		node.childNodes.length === 1 &&
		node.childNodes[0].nodeType === Node.TEXT_NODE
	);

	if (!valid) {
		throw new Error(`This transition only works on elements with a single text node child`);
	}

	const text = node.textContent;
	const duration = text.length * speed;

	return {
		duration,
		tick: t => {
			const i = ~~(text.length * t);
			node.textContent = text.slice(0, i);
		}
	};
}
```
