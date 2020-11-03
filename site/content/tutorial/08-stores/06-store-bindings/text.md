---
title: Store 绑定
---

如果一个 Store 是可写入的 -- 也就是说它有一个 `set` 方法 -- 你就可以对它的值进行绑定，就像你可以对本地组件的状态进行绑定一样。

在这个例子中，我们有一个可写入 Store `name` 和一个衍生 Store `greeting`。更新 `<input>` 元素。

```html
<input bind:value={$name}>
```

Changing
改变输入值就会马上更新 `name` 和所有要用到它的值。

我们也可以直接对处于一个组件内部的存储值进行赋值。添加一个 `<button>` 元素。
```html
<button on:click="{() => $name += '!'}">
	Add exclamation mark!
</button>
```

The `$name += '!'` assignment is equivalent to `name.set($name + '!')`.