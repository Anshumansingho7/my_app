<script>
  import Footer from "$lib/components/Footer.svelte";
  import Header from "$lib/components/Header.svelte";
</script>

<style>
  /* Ensure main content takes full height */
  main {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }
  
  /* Ensuring no extra space is added */
  .container {
    flex: 1; /* Make sure content fills remaining space */
  }
</style>

<!-- This works as a partial -->
<Header />
<main class="container">
  <slot />
</main>
<Footer />
