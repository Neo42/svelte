---
title: @debug 标签
---

有时候，在数据流经您的应用程序时对其进行检查会很有用。

一种方法是在标记内使用`console.log(...)`。 但如果你想要暂停执行，可以将`{@debug ...}`标记与一个要检查的值组成的、以逗号分隔的列表一起使用：

```html
{@debug user}

<h1>Hello {user.firstname}!</h1>
```

现在如果你打开你的开发者工具并开始与 `<input>` 元素进行交互的话，你就会在 `user` 发生改变时触发调试器。