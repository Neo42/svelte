---
title: 声明
---

Svelte 会在你的组件的状态发生变化时自动更新 DOM。通常情况下，组件状态中的某些部分需要从 _其他_ 部分计算出来（比如从 `firstname` 和 `lastname` 派生出来的 `fullname`），并在它们发生变化时重新计算。

对于这些情况，我们可以用 _反应式声明_ 。它们看起来像这样：

```js
let count = 0;
$: doubled = count * 2;
```

> 如果这看起来有点陌生，不用担心。这是[语法正确](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/label)的 JavaScript（即使不那么常见），Svelte 会把它解释为 "每当任何被引用到的值发生变化时，就重新运行这段代码"。一旦你习惯了，就再也不会不想用这个功能了。

我们来在标记中使用 `doubled` ：

```html
<p>{count} doubled is {doubled}</p>
```

当然，你也可以直接在标记中写 `{count * 2}` 而不这样写--你不一定要使用响应式的值。响应式的值会在你需要多次引用它们或你有多个依赖于其他反应值的值时变得特别有价值。
