<script>
  import "../app.css"
  let currentPage = "home"
</script>

<svelte:head>
  <meta name="robots" content="noindex" />
</svelte:head>

<div class="container">
  <nav>
    <a href="." class="logo" on:click={() => (currentPage = "home")}
      >SvelteKit Avatar</a
    >
    <div class="menu">
      <a
        href="."
        class={currentPage === "home" ? "active" : ""}
        on:click={() => (currentPage = "home")}>Home</a
      >
      <a
        href="."
        class={currentPage === "about" ? "active" : ""}
        on:click={() => (currentPage = "about")}>About</a
      >
    </div>
  </nav>

  <slot />
</div>

<style>
  .container {
    margin: auto;
    max-width: 680px;
  }
  nav {
    padding-top: 1rem;
    display: flex;
    justify-content: space-between;
  }
  .logo {
    position: relative;
    color: hsl(202, 4%, 41%);
  }
  .active {
    text-decoration: underline;
  }
  .logo::after {
    content: "beta";
    position: absolute;
    top: -0.8rem;
    right: -1.5rem;
    font-size: 0.7rem;
    letter-spacing: 0.5px;
    padding: 0.1rem 0.4rem;
    background-color: rgb(230, 214, 245);
    color: blueviolet;
    border-radius: 6px;
  }
  .menu {
    display: flex;
    gap: 1.5rem;
  }
  a {
    text-decoration: none;
    color: black;
    font-weight: 500;
  }
</style>
