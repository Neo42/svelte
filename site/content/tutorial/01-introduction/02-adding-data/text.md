---
title: 添加数据
---

一个只渲染一些静态标记的组件并不是很有意思。让我们添加一些数据吧。

首先，在你的组件中添加一个 script 标签并声明一个 `name` 变量。

```html
<script>
	let name = "world";
</script>

<h1>Hello world!</h1>
```

然后，我们就可以在标记中引用 `name` 了。

```html
<h1>Hello {name}!</h1>
```

我们可以在大括号里写任何我们想要的 JavaScript。试着把 `name` 改成 `name.toUpperCase()`，来个更响亮的问候语吧。
