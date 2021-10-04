<script context="module">
  export async function load({ fetch, page }) {
    const { lastName } = page.params
    const res = await fetch(`/api/${lastName}`)

    if (!res.ok) return { status: res.status, error: new Error() }

    return {
      props: {
        user: await res.json(),
      },
    }
  }
</script>

<script>
  export let user
  import { fade } from "svelte/transition"

  const fullName = `${user.firstName} ${user.lastName}`

  const goBack = () => {
    window.history.back()
  }
</script>

<svelte:head>
  <title>Profile for {fullName}</title>
</svelte:head>
<main>
  <h1>{fullName}</h1>

  <div class="box" in:fade>
    <img src={user.avatar} alt={user.lastName} />
    <ul>
      <li><span>Title</span> {user.title}</li>
      <li><span>Phone</span> {user.phone}</li>
      <li><span>Email</span> {user.email}</li>
    </ul>
  </div>
  <button on:click={goBack}>Back</button>
</main>

<style>
  main {
    padding: 2rem 0;
  }
  button {
    border: 1px solid #e2e2e2;
    padding: 0.25rem 0.5rem;
    cursor: pointer;
    background-color: #f1f1f1;
    color: #222323;
    margin: 2rem auto;
    display: block;
  }
  button:active {
    background-color: #e2e2e2;
  }
  h1 {
    font-size: 2rem;
    letter-spacing: -1px;
    color: black;
    margin-top: 0;
    text-align: center;
  }
  .box {
    display: flex;
    flex-direction: column;
    gap: 2rem;
    align-items: center;
  }
  img {
    width: 100%;
    max-width: 6rem;
  }
  ul {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  li {
    font-size: 1rem;
    display: flex;
    align-items: center;
    gap: 1rem;
    padding: 0.5rem 0;
    border-bottom: 1px solid #f0f6f0;
  }
  li:last-of-type {
    border: 0;
  }
  span {
    font-size: 1rem;
    color: #ccc;
    min-width: 60px;
  }
</style>
