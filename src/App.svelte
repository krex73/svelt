<script>
  import { writable } from "svelte/store";
  import { Tween } from "svelte/motion";
  import { cubicOut } from "svelte/easing";
  const menuOpened = writable(false);
  let menuLeft = new Tween(-30, {
    duration: 200,
    easing: cubicOut,
  });
  let mainLeft = new Tween(0, {
    duration: 200,
    easing: cubicOut,
  });
  const openMenu = () => {
    menuLeft.set(0);
    mainLeft.set(20); // not 30 to give a parallax kind of effect
    menuOpened.set(true);
  };
  const closeMenu = () => {
    menuLeft.set(-30);
    mainLeft.set(0);
    menuOpened.set(false);
  };
</script>

<div class="main" style="left: {mainLeft.current}vw;">
  <h1>Main panel</h1>
  <p>This is a sample of Svelte app with an animated side menu.</p>
  {#if !$menuOpened}
    <div onclick={openMenu} class="hamburger">
      <div class="btn__hamb">
        <div></div>
      </div>
    </div>

    <!-- <button on:click={() => openMenu()}>
		Open Menu
	</button> -->
  {/if}
</div>
<div class="menu" style="left: {menuLeft.current}vw;">
  <h2>Menu</h2>
  <p>Here are the menu contents. Kind of empty at the moment.</p>
  {#if $menuOpened}
    <button onclick={closeMenu}> Close Menu </button>
  {/if}
</div>

<style>
  /* * {
    box-sizing: border-box;
    color: #555;
  } */
  div.menu {
    background: #ff7000;
    width: 30vw;
    height: 100vh;
    position: absolute;
    top: 0;
    left: 0;
    /* padding: 5vh 5vw; */
    z-index: 1;
  }
  div.main {
    background: rgba(120, 0, 100, 0.3);
    width: 100vw;
    height: 100vh;
    position: absolute;
    top: 0;
    left: 0;
    /* padding: 5vh 15vw; */
  }
  .hamburger {
    position: relative;
    display: inline-block;
    vertical-align: middle;
    cursor: pointer;
    width: 40px;
    height: 40px;
    border: 1px solid #0e7318;
    background: #fff;
    padding: 5px;
    border-radius: 8px;
  }

  .btn__hamb {
    position: relative;
    display: block;
    width: 100%;
    height: 4px;
    background: #0e7318;
    cursor: pointer;
  }
  .btn__hamb div {
    width: 100%;
    height: 100%;
  }
  .btn__hamb:before,
  .btn__hamb:after {
    content: "";
    width: 100%;
    height: 100%;
    position: absolute;
    left: 0;
    background: #0e7318;
  }
  .btn__hamb:before {
    top: -8px;
  }
  .btn__hamb:after {
    top: 8px;
  }
</style>
