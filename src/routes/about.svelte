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
    font-size: 1rem;
    padding: 2rem 0;
    text-align: center;
  }
  h1 {
    font-size: 2rem;
    letter-spacing: -1px;
    color: black;
    margin-top: 0;
  }
</style>
