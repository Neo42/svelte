---
title: 导出
---

从 `context ="module"` 脚本块导出的所有内容都将成为这个模块本身的一个导出内容。 如果我们从 `AudioPlayer.svelte` 中导出一个 `stopAll` 函数...

```html
<script context="module">
  const elements = new Set();

  export function stopAll() {
    elements.forEach(element => {
      element.pause();
    });
  }
</script>
```

...然后我们可以从 `App.svelte` 中把它导入进来...

```html
<script>
  import AudioPlayer, { stopAll } from './AudioPlayer.svelte';
</script>
```

...并在事件处理程序中使用它：

```html
<button on:click="{stopAll}">stop all audio</button>
```

> 你不能使用默认导出，因为组件 *就是* 默认导出。
