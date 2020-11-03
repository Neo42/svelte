---
title: 默认值
---

我们可以很容易地在 `Nested.svelte` 中为 Props 指定默认值。

```html
<script>
	export let answer = "a mystery";
</script>
```

如果我们现在再添加一个 _不带_ `answer` prop 的组件，它将回到默认值。

```html
<Nested answer="{42}" /> <Nested />
```
