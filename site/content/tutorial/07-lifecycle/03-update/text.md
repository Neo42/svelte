---
title: beforeUpdate 和 afterUpdate
---

`beforeUpdate` 函数可以把动作安排在 DOM 即将更新时进行。`afterUpdate` 则与它对应，一旦DOM与你的数据同步后，用于运行代码。

把它们结合在一起用的话，对于做一些单纯依靠状态驱动的方式很难做到的事情非常有用，比如更新元素的滚动位置。

这个 [Eliza](https://en.wikipedia.org/wiki/ELIZA) 聊天机器人用起来很烦人，因为你得不停地滚动聊天窗口。我们来解决一下这个问题。

```js
let div;
let autoscroll;

beforeUpdate(() => {
	autoscroll = div && (div.offsetHeight + div.scrollTop) > (div.scrollHeight - 20);
});

afterUpdate(() => {
	if (autoscroll) div.scrollTo(0, div.scrollHeight);
});
```

请注意，`beforeUpdate` 将在组件挂载之前首先运行，因此我们需要在读取 `div` 属性之前检查一下它是否存在。