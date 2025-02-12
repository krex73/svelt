<script lang="ts">
  import Menu from "./lib/Menu.svelte";
</script>

<main>
  <Menu />
  <div class="main">
    Lorem ipsum dolor sit amet consectetur adipisicing elit. Rerum delectus,
    accusamus iusto eum veniam blanditiis saepe aspernatur deleniti ullam nam
    facere fuga, ipsam ducimus quaerat doloribus aperiam, porro quisquam
    perferendis!
  </div>
</main>

<style>
  .main {
    width: 100vw;
    height: 100vh;
    position: absolute; 
    top: 0;
    left: 0;
    z-index: 0;
  }
</style>
