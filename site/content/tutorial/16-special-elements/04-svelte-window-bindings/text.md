---
title: <svelte:window> bindings
---

我们也可以对 `window` 的某些属性进行绑定，比如`scrollY`。更新第7行：

```html
<svelte:window bind:scrollY={y}/>
```

你可以绑定的属性列表如下：

* `innerWidth`
* `innerHeight`
* `outerWidth`
* `outerHeight`
* `scrollX`
* `scrollY`
* `online` — an alias for `window.navigator.onLine`

除了 `scrollX` 和 `scrollY` 之外，其他属性都是只读的。