<script>
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

<main class="container">
  <slot />
</main>
