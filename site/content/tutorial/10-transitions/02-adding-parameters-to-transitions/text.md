---
title: 添加参数
---

过渡函数可以接受参数。 用 `fly` 代替 `fade` 过渡...

```html
<script>
	import { fly } from 'svelte/transition';
	let visible = true;
</script>
```

...并把它与一些选项一起应用到 `<p>` 上。

```html
<p transition:fly="{{ y: 200, duration: 2000 }}">
	Flies in and out
</p>
```

请注意，过渡是 _可逆的_ --如果你在过渡进行时点击复选框，它将从当前点开始过渡，而不是从开头或末尾。