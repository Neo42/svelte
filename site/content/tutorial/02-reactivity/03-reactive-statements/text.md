---
title: 断言
---

我们不只能声明响应式的值--我们还能响应式地运行任意语句。比如，每当 count 的值发生变化时，我们就可以将打印出来。

```js
$: console.log(`the count is ${count}`);
```

你可以很容易地用一个代码块把断言组合在一起。

```js
$: {
	console.log(`the count is ${count}`);
	alert(`I SAID THE COUNT IS ${count}`);
}
```

你甚至可以把 `$:` 放在 `if` 代码块之类的东西前面。

```js
$: if (count >= 10) {
	alert(`count is dangerously high!`);
	count = 9;
}
```
