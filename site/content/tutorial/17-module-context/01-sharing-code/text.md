---
title: 分享代码
---

在我们目前所看到的所有例子中，`<script>`块包含了当每个组件实例被初始化时运行的代码。对于绝大多数的组件来说，这就是你所需要的全部。

你会在极少数情况下需要在一个单独的组件实例之外运行一些代码。例如，你可能会同时播放所有五个音频播放器；如果播放一个播放器会使其他所有播放器停止就更好了。

我们可以通过声明一个`<script context="module">`块要实现这个功能。它里面的代码将在模块第一次解析时运行一次，而不是在组件实例化时运行。把它放在`AudioPlayer.svelte`的顶部：

```html
<script context="module">
	let current;
</script>
```

现在我们不需要任何状态管理，就可以让组件之间相互 "对话"了。

```js
function stopOthers() {
	if (current && current !== audio) current.pause();
	current = audio;
}
```
