---
title: animate 指令
---

在[上一章](tutorial/deferred-transitions)中，我们使用延迟过渡创建了元素从一个待办清单移动到另一个待办清单时的运动错觉。

为了把这个错觉做完，我们还需要为那些 *不带* 过渡的元素制作运动。为此，我们使用 `animate` 指令。

首先，从`svelte/animate`中导入`flip`函数--flip代表['First, Last, Invert, Play'](https://aerotwist.com/blog/flip-your-animations/) 。

```js
import { flip } from 'svelte/animate';
```

然后把它添加到`<label>`元素中：

```html
<label
	in:receive="{{key: todo.id}}"
	out:send="{{key: todo.id}}"
	animate:flip
>
```

这样的话，运动速度有点慢，所以我们可以添加一个`duration`参数。

```html
<label
	in:receive="{{key: todo.id}}"
	out:send="{{key: todo.id}}"
	animate:flip="{{duration: 200}}"
>
```

> `duration` 也可以是 `d => milliseconds` 函数，其中 `d` 是元素必须移动的像素数。

请注意，所有的过渡和动画都是用 CSS 而不是 JavaScript 实现的，这意味着它们不会阻塞主线程（或被主线程阻塞）。