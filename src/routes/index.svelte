<script context="module">
  export async function load({ fetch }) {
    const res = await fetch("/api")

    if (!res.ok)
      return {
        status: res.status,
        error: new Error(),
      }

    return {
      props: {
        users: await res.json(),
      },
    }
  }
</script>

<script>
  export let users

  import { fly } from "svelte/transition"
  import { cubicIn } from "svelte/easing"
</script>

<svelte:head>
  <title>SvelteKit Avatar — A website to find user profiles.</title>
</svelte:head>
<main>
  {#each users as { avatar, lastName }, index}
    <a
      sveltekit:prefetch
      href={`/${lastName}`}
      class="box"
      in:fly={{ y: 50, delay: index * 20, duration: 100, ease: cubicIn }}
    >
      <img src={avatar} alt={lastName} />
      <h2>{lastName}</h2>
    </a>
  {/each}
</main>

<style>
  main {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
    margin: 2rem 0;
    background: #f0f6f0;
    border-top: 1px solid #f0f6f0;
    border-left: 1px solid #f0f6f0;
  }
  .box {
    padding: 1.5rem;
    overflow: hidden;
    text-align: center;
    border-right: 1px solid #f0f6f0;
    border-bottom: 1px solid #f0f6f0;
    background: white;
    transition: box-shadow 150ms ease-in-out, transform 200ms ease-in-out;
  }
  .box:hover {
    box-shadow: 0 10px 40px rgba(0, 0, 0, 0.05);
    transform: translateY(-8px) translateX(-8px);
  }
  h2 {
    font-size: 0.75rem;
    font-weight: 400;
    margin-block: 0.5rem;
  }
  a {
    text-decoration: none;
    color: gray;
  }
  img {
    width: 100%;
    max-width: 100%;
    object-fit: contain;
  }
</style>
