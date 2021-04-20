<script>
  import Router from "svelte-spa-router";
  import routes from "../src/routes/routes";
  import Nav from "./components/global/nav.svelte";
</script>

<main>
  <Nav />
  <Router {routes} />
</main>

<style>
</style>
