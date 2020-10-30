---
title: 媒体元素
---

`<audio>` 和 `<video>` 元素中有一些你可以做绑定的属性。这个例子演示了其中的几个。

在第116行添加`currentTime={time}`、`duration`和`paused`绑定：

```html
<video
	poster="https://sveltejs.github.io/assets/caminandes-llamigos.jpg"
	src="https://sveltejs.github.io/assets/caminandes-llamigos.mp4"
	on:mousemove={handleMousemove}
	on:mousedown={handleMousedown}
	bind:currentTime={time}
	bind:duration
	bind:paused
></video>
```

> `bind:duration` 相当于 `bind:duration={duration}`。

现在，当你点击视频时，它会根据情况更新 `time` 、`duration` 和 `paused`。这意味着我们可以用它们来构建自定义控件。

> 通常在网络上，你会通过监听 `timeupdate` 事件来跟踪 `currentTime`。但是这些事件发生的频率太低，导致用户界面不稳定。Svelte做得更好--它使用 `requestAnimationFrame` 来检查 `currentTime`。

`<audio>` 和 `<video>` 的完整绑定如下--六个 _只读_ 绑定...：

* `duration` (只读) — 视频的总长度，以秒为单位
* `buffered` (只读) — 一个 `{start, end}` 对象组成的数组
* `seekable` (只读) — 同上
* `played` (只读) — 同上
* `seeking` (只读) — 布尔值
* `ended` (只读) — 布尔值

...和五个 _双向_ 绑定。

* `currentTime` — 视频中的当前点，以秒为单位
* `playbackRate` — 播放视频的速度，其中 `1` 为 "正常"
* `paused` — 这个不用说了吧（布尔值）
* `volume` — 一个在0和1之间的值。
* `muted` — 一个布尔值，true为静音。

视频还有只读的`videoWidth`和`videoHeight`属性可以做绑定。