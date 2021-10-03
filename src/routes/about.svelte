<script context="module">
  export const prerender = true
</script>

<script>
  import { fade } from "svelte/transition"
</script>

<svelte:head>
  <title>About Page — SvelteKit Avatar</title>
</svelte:head>

<main in:fade>
  <h1>About Page</h1>
  <p>A website to find user profiles.</p>
</main>

<style>
  main {
    font-size: 1.5rem;
    justify-content: center;
  }
  h1 {
    color: black;
  }
</style>
