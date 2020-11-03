---
title: 衍生 Store 
---

你可以用 `derived` 创建出这样一个 Store ，它的值基于一个或多个 _其他_ Store 的值。在上一个例子的基础上，我们可以创建一个推衍出页面打开时间的 Store 。

```js
export const elapsed = derived(
	time,
	$time => Math.round(($time - start) / 1000)
);
```

> 我们也可以由多个输入衍生出一个 Store ，并显式地 `set` 一个值，而不返回它（这对异步推衍值很有用）。更多信息请查看[API参考](docs#derived)。
