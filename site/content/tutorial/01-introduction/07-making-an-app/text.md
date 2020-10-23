---
title: 制作一个应用程序
---

这个教程旨在让你熟悉编写组件的过程。但在某些时候，你会想在自己的文本编辑器中开始编写组件。

首先，你需要把 Svelte 和一个构建工具整合起来。 这里有官方维护的 [Rollup](https://rollupjs.org) 和 [webpack](https://webpack.js.org/) 插件...

- [rollup-plugin-svelte](https://github.com/sveltejs/rollup-plugin-svelte)
- [svelte-loader](https://github.com/sveltejs/svelte-loader)

...还有各种各样的[社区维护插件](https://github.com/sveltejs/integrations#bundler-plugins)。

如果你对 web 开发还比较陌生而且并没有使用过这些工具，也不要担心。我们准备了一个简单的分步骤指南，[给新开发者的 Svelte](blog/svelte-for-new-developers)，它将带你走完这整个过程。

你还需要配置你的文本编辑器。如果你使用的是 VS Code，就安装[Svelte 扩展](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode)，或者按照[这个指南](blog/setting-up-your-editor)把你的文本编辑器配置成将 `.svelte` 文件与 `.html` 同等对待，从而实现语法高亮。

然后，只要你设置好了你的项目，使用 Svelte 组件就很容易了。编译器会把每个组件变成一个普通的 JavaScript 类 -- 直接导入它并使用 `new` 实例化：

```js
import App from "./App.svelte";

const app = new App({
	target: document.body,
	props: {
		// 我们之后会了解 props
		answer: 42,
	},
});
```

如果需要的话，你之后可以使用[组件 API](docs#Client-side_component_API)与 `app` 进行交互。
