---
title: <svelte:options>
---

最后，`<svelte:options>` 可以让你指定编译器的选项。

我们就拿 `immutable` 选项举例。在这个应用程序中，每当收到新数据时， `<Todo>` 组件就会闪烁。点击其中一个项目，通过创建一个更新的 `todos` 数组来切换其 `done` 状态。这将导致*其他*几个 `<Todo>` 项即使最终没有对 DOM 做任何改变也会闪烁。

我们可以通过让 `<Todo>` 组件接收*不可变*的数据来对这种情况进行优化。这意味着我们承诺永远不*改变* `todo` prop，而在变化发生时创建新的todo对象。

把这个添加到`Todo.svelte`文件的顶部。

```html
<svelte:options immutable={true}/>
```

> 如果你喜欢的话，可以把它缩短为`<svelte:options immutable/>`。

现在，当你点击todos时，只有被更新的组件才会闪烁。

这里可以设置的选项有

* `immutable={true}` - 永远不使用可变数据，所以编译器可以通过简单地检查引用相等性来确定值是否发生了变化。
* `immutable={false}` - 默认值。Svelte 对可变对象是否发生变化比较保守。
* `accessors={true}` - 为组件的道具添加 getter 和 setter 。
* `accessors={false}` - 默认值。
* `namespace="..."` - 其中使用该组件的命名空间，最常见的是`"svg"`。
* `tag="..."` - 在把该组件编译为自定义元素时要使用的名称。

想了解这些选项的更多信息，请查阅[API参考](docs)。
