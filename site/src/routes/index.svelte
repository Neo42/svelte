<script>
  import { Blurb, Hero, Section } from '@sveltejs/site-kit'
  import Contributors from './_components/Contributors.svelte'
  import Example from './_components/Example.svelte'
  import WhosUsingSvelte from './_components/WhosUsingSvelte.svelte'
  // import Lazy from '../components/Lazy.svelte';

  // TODO this causes a Sapper CSS bug...
  // function loadReplWidget() {
  // 	console.log('lazy loading');
  // 	return import('../components/Repl/ReplWidget.svelte').then(mod => mod.default);
  // }
</script>

<style>
  /* darken text for accessibility */
  /* TODO does this belong elsewhere? */
  :global(.back-light) {
    --text: hsl(36, 3%, 44%);
  }

  .examples {
    background: var(--second);
    color: white;
    overflow: hidden;
  }
</style>

<svelte:head>
  <title>Svelte • 赛博强化型 web 应用程序</title>

  <meta name="twitter:title" content="Svelte" />
  <meta name="twitter:description" content="赛博强化型 web 应用程序" />
  <meta name="Description" content="赛博强化型 web 应用程序" />
</svelte:head>

<Hero
  title="Svelte"
  tagline="赛博强化型 web 应用程序"
  outline="svelte-logo-outline.svg"
  logotype="svelte-logotype.svg" />

<Blurb>
  <a href="blog/write-less-code" slot="one">
    <h2>编写更少的代码</h2>
    <p>用你已经掌握的语言—— HTML 、 CSS 和 JavaScript 来构建没有样板的组件</p>

    <span class="learn-more">了解更多</span>
  </a>

  <a href="blog/virtual-dom-is-pure-overhead" slot="two">
    <h2>没有虚拟 DOM</h2>
    <p>
      Svelte将你的代码编译成精炼无框架的原生 JS
      ，使你的应用程序启动速度快、一直速度快。
    </p>

    <span class="learn-more">了解更多</span>
  </a>

  <a href="blog/svelte-3-rethinking-reactivity" slot="three">
    <h2>真正的响应能力</h2>
    <p>不再需要复杂的状态管理库-- Svelte 为 JavaScript 本身赋予响应能力。</p>

    <span class="learn-more">了解更多</span>
  </a>

  <div class="description" slot="what">
    <p>
      Svelte是一种全新的构建用户界面的方法。React 和 Vue
      等传统框架是把大部分工作放在
      <em>浏览器</em>
      中进行，而Svelte则是将这些工作转移到跟你构建应用程序同时发生的
      <em>编译阶段</em>
      中。
    </p>

    <p>
      与其采用虚拟 DOM 比较差异的做法，Svelte
      写出的代码会在你的应用程序状态发生变化时以手术刀般的精度更新 DOM 。
    </p>

    <p>
      <a href="blog/svelte-3-rethinking-reactivity">阅读这篇介绍性博客文章</a>
      来了解更多。
    </p>
  </div>

  <div
    style="grid-area: start; display: flex; flex-direction: column; min-width: 0"
    slot="how">
    <pre
      class="language-bash"
      style="margin: 0 0 1em 0; min-width: 0; min-height: 0">
      npx degit
      <a
        href="https://github.com/sveltejs/template"
        style="user-select: initial;">
        sveltejs/template
      </a>
      my-svelte-project
      <span class="token comment">
        # 或者下载并解压
        <a href="https://github.com/sveltejs/template/archive/master.zip">
          这个 .zip 文件
        </a>
      </span>
      cd my-svelte-project npm install npm run dev
    </pre>

    <p style="flex: 1">
      查看这篇
      <a href="blog/the-easiest-way-to-get-started">快速开始指南</a>
      了解更多信息。
    </p>

    <p class="cta">
      <a rel="prefetch" href="tutorial">学习 Svelte</a>
    </p>
  </div>
</Blurb>

<div class="examples">
  <Example id="hello-world">
    <p>Svelte 组件是在 HTML 的基础上构建的。试试添加数据。</p>
  </Example>

  <Example id="nested-components">
    <p>
      CSS 默认只在它所在的组件内部起作用 —
      再也不会有样式冲突和优先级战争了。你也可以
      <a href="/blog/svelte-css-in-js">使用你最喜欢的 CSS-in-JS 库</a>
      .
    </p>
  </Example>

  <Example id="reactive-assignments">
    <p>通过给局部变量赋值来触发高效而细粒度的更新。把剩下的都交给编译器。</p>
  </Example>

  <Example id="svg-transitions">
    <p>用强大而高性能的框架内置过渡引擎构建漂亮的用户界面。</p>
  </Example>
</div>

<Section>
  <h3>谁在使用 Svelte ?</h3>

  <WhosUsingSvelte />
</Section>

<Section>
  <h3>贡献者</h3>

  <p>
    Svelte 是免费的开源软件，是一群志愿者的努力使它成为可能。
    <a href="https://github.com/sveltejs/svelte">加入我们!</a>
  </p>

  <Contributors />
</Section>
