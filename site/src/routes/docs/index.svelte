<script context="module">
  export async function preload() {
    const sections = await this.fetch(`docs.json`).then((r) => r.json())
    return { sections }
  }
</script>

<script>
  import { Docs } from '@sveltejs/site-kit'

  export let sections
</script>

<svelte:head>
  <title>API 文档 • Svelte</title>

  <meta name="twitter:title" content="Svelte API docs" />
  <meta name="twitter:description" content="赛博强化型 web 应用程序" />
  <meta name="Description" content="赛博强化型 web 应用程序" />
</svelte:head>

<Docs {sections} />
