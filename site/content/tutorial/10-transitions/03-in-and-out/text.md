---
title: in 和 out
---

元素中可以使用一个 `in` 或 `out` 指令，或者两者一起使用，这样可以替换 `transition` 指令的使用。导入 `fly` 和 `fade`...

```js
import { fade, fly } from 'svelte/transition';
```

.然后将 `transition` 指令替换为单独的 `in` 和 `out` 指令。

```html
<p in:fly="{{ y: 200, duration: 2000 }}" out:fade>
	Flies in, fades out
</p>
```

这样的话，过渡就是 _不可逆_ 的。