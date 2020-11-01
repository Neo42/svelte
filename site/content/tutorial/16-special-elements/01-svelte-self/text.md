---
title: <svelte:self>
---

Svelte提供了多种内置元素。第一个是 `<svelte:self>` ，可以让一个组件递归式地包含它自己。

它对于像文件夹树视图之类的东西很有用，这样文件夹就可以包含*其他*文件夹。在`Folder.svelte`中，我们希望能这样...

```html
{#if file.type === 'folder'}
	<Folder {...file}/>
{:else}
	<File {...file}/>
{/if}
```

...但这是不可能的，因为一个模块不能导入它自己。换种方法，我们使用`<svelte:self>`：

```html
{#if file.type === 'folder'}
	<svelte:self {...file}/>
{:else}
	<File {...file}/>
{/if}
```
