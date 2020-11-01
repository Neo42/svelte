---
title: <svelte:component>
---

一个组件可以用`<svelte:component>`完全改变它的类别。与其使用一连串的`if`块...

```html
{#if selected.color === 'red'}
	<RedThing/>
{:else if selected.color === 'green'}
	<GreenThing/>
{:else if selected.color === 'blue'}
	<BlueThing/>
{/if}
```

...我们可以使用一个单一的动态组件：

```html
<svelte:component this={selected.component}/>
```

`this`值可以是任何组件构造函数，也可以是一个 falsy 值--如果是 falsy，就不会显示组件。