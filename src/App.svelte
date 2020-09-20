<script>
  import Navbar from "./app/Sections/Navbar.svelte";
  import Kanban from "./app/Sections/Kanban.svelte";
  import Footer from "./app/Sections/Footer.svelte";
</script>

<Navbar />

<main>
  <Kanban />
</main>

<Footer />

<style global lang="scss">
  main {
    padding: 1rem;
  }
</style>
