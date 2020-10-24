---
title: 更新数组和对象
---

因为 Svelte 的反应能力是通过赋值触发的，所以使用 `push` 和 `splice` 等数组方法并不会自动引起更新。比如，点击这个按钮就不会有任何效果。

解决这个问题的方法之一是增加一个原本多余的赋值。

```js
function addNumber() {
	numbers.push(numbers.length + 1);
	numbers = numbers;
}
```

但我们有一个更加约定俗成的解决方案。

```js
function addNumber() {
	numbers = [...numbers, numbers.length + 1];
}
```

你可以用类似的模式来替换 `pop`, `shift`, `unshift` 和 `splice`。

给数组和对象的 _属性_ 赋值--例如 `obj.foo += 1` 或 `array[i] = x` --与给值本身赋值的做法类似。

```js
function addNumber() {
	numbers[numbers.length] = numbers.length + 1;
}
```

一个简单的经验法则：被更新的变量名必须在赋值的左侧。比方说这样...

```js
const foo = obj.foo;
foo.bar = "baz";
```

...并不会更新对 `obj.foo.bar` 的引用，除非你在后面写上 `obj = obj`。
