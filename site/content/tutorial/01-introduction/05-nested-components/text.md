---
title: 嵌套组件
---

如果我们把整个应用程序都放在一个组件中，那将是不切实际的。相反，我们可以从其他文件中导入组件，并像包含元素一样包含它们。

添加一个导入 `Nested.svelte` 的 `<script>` 标签...

```html
<script>
	import Nested from "./Nested.svelte";
</script>
```

...然后把它添加到标记中:

```html
<p>This is a paragraph.</p>
<Nested />
```

请注意，尽管 `Nested.svelte` 有一个 `<p>` 元素，但 `App.svelte` 的样式并没有泄露进来。

还有请注意，组件名称 `Nested` 是大写的。采用这个惯例是为了让我们能够区分用户定义的组件和一般的 HTML 标签。
