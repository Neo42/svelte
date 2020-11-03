---
title: tweened
---

设置数值并看着DOM自动更新很酷。知道更酷的是什么吗？就是用这些值*制作 Tweening*。Svelte中囊括了一些工具，可以帮助你构建使用动画来传达变化的顺滑用户界面。

我们先把 `progress` Store 改为 `tweened`。

```html
<script>
	import { tweened } from 'svelte/motion';

	const progress = tweened(0);
</script>
```

点击按钮就会导致进度条发生动画，到达其新值。不过这有点不自然，不太让人满意。我们需要增加一个缓动函数。

```html
<script>
	import { tweened } from 'svelte/motion';
	import { cubicOut } from 'svelte/easing';

	const progress = tweened(0, {
		duration: 400,
		easing: cubicOut
	});
</script>
```


> `svelte / easing` 模块中囊括了[Penner缓动函数](https://web.archive.org/web/20190805215728/http://robertpenner.com/easing/)，或者你也可以使用自己的 `p => t` 函数，其中 `p` 和 `t` 都是介于 0 和 1 之间的值。

`tweened` 全部的可用选项：

* `duration`----以毫秒为单位的tween持续时间，或 `(from, to) => milliseconds`函数，允许你(例如)为较大的数值变化指定更长的动画。
* `easing` -- -- 一个 `p => t` 函数
* `interpolate`--一个自定义的 `(from, to)=> t => value` 函数，用于对任意值进行插值。默认情况下，Svelte会对数字、日期和相同形状的数组和对象进行插值（只要它们只包含数字和日期或其他有效的数组和对象）。如果你想对（比如）颜色字符串或变换矩阵进行插值，请提供一个自定义的插值函数。

你也可以将这些选项作为第二个参数传给 `progress.set` 和 `progress.update` ，这样的话，它们将覆盖默认值。`set` 和 `update` 方法都返回一个 promise，当动画完成时，这个 promise 会进行决议。
