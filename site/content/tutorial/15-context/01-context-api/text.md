---
title: setContext 和 getContext
---

Context API 提供了一种机制，让组件之间可以相互 "对话" 而不需要把数据和函数作为 props 传递，也不需要分发大量的事件。这是一个高级的功能，但是很有用。

以这个使用[Mapbox GL](https://docs.mapbox.com/mapbox-gl-js/overview/)地图的示例应用为例。我们想使用 `<MapMarker>` 组件来渲染标记，但我们并不希望把一个对底层的 Mapbox 实例的引用作为 Contextprop 传递给每一个组件。

Context API有两半-- `setContext` 和 `getContext` 。如果一个组件调用了 `setContext(key，context)`，那么它的所有*子*组件都可以用 `const context = getContext(key)`来检索 Context。

我们先设置 Context 。在 `Map.svelte` 中，从 `svelte` 导入 `setContext` ，从 `mapbox.js` 导入 `key`，然后调用 `setContext`。

```js
import { onMount, setContext } from 'svelte';
import { mapbox, key } from './mapbox.js';

setContext(key, {
	getMap: () => map
});
```

Context 对象可以是任何你喜欢的东西。像[生命周期函数](tutorial/onmount)一样，`setContext` 和 `getContext` 必须在组件初始化过程中被调用；由于 `map` 直到在组件挂载才会被创建，我们的 Context 对象需要包含一个 `getMap` 函数，而不是 `map` 本身。

而另一方面，在`MapMarker.svelte`中，现在我们就可以拿到Mapbox实例的引用了。

```js
import { getContext } from 'svelte';
import { mapbox, key } from './mapbox.js';

const { getMap } = getContext(key);
const map = getMap();
```

现在标记就可以把自己添加到地图上了。

> `<MapMarker>`更完善的版本还会处理标记的移除和 props 的更改，但我们在这里只是在演示 Context 。

## Context 键

在`mapbox.js`中你会看到这一行：

```js
const key = {};
```

我们可以把任何东西作为键使用——比如，我们可以这样 `setContext('mapbox', ...)`。使用字符串的缺点是，不同的组件库可能会意外使用同一个字符串；使用对象字面量可以保证键在任何情况下都不会相互冲突（因为一个对象只对它自己有引用上的平等，即 `{} !=={}` 而 `"x"==="x"` ），甚至当你有多个不同的 context 在多个组件层中运行时也不会。

## Context vs Store 

Context 和 Store 看起来很像。它们的不同之处在于， Store 可以在应用程序的*任何*部分使用，而 Context 只能在*组件和其子组件中*使用。如果你在使用一个组件的多个实例时，不希望让一个实例的状态影响到其他实例的状态，那么这一点就会很有帮助。

其实，你有可能可以把这两个实例一起使用。因为 Context 不是响应式的，所以随时间变化的值应该用 Store 来表示。

```js
const { these, are, stores } = getContext(...);
```
