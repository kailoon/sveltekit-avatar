<script>
  import "../app.css"
</script>

<svelte:head>
  <meta name="robots" content="noindex" />
</svelte:head>

<nav>
  <a href="." class="logo">SvelteKit Avatar</a>
  <div class="menu">
    <a href=".">Home</a>
    <a href="/about">About</a>
  </div>
</nav>

<slot />

<style>
  nav {
    padding-top: 1rem;
    display: flex;
    justify-content: space-between;
  }
  .logo {
    position: relative;
    color: hsl(202, 4%, 41%);
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
