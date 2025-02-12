<script lang="ts">
  let open = $state<boolean>(false);
  // import { fly } from "svelte/transition";

  let showMenu = () => {
    open = true;
    console.log("ddd");
  };

  let hideMenu = () => {
    open = false;
    console.log("ddd");
  };
</script>

<!--Кнопка-->
<button
  onclick={showMenu}
  aria-label="Меню"
  class="hamburger"
  id="mobile-menu-btn"
>
  <div class="btn__hamb"></div>
</button>

<!--Мобильное меню-->
<div class="mobile-menu" id="mobile-menu">
  <div class="mm__bg mm__close"></div>
  <div class="mm__wrapper" class:open id="mm__wrapper">
    <div class="mm__header">
      <span class="close-btn close-btn--red mm__close"></span>
      <a href="/" class="h__logo">g</a>
    </div>
  </div>
</div>

<style>
  /* .zvet {
    color: var(--color);
    font-size: small;
  } */

  /*Стили кнопки*/
  .hamburger {
    z-index: 2;
    position: relative;
    display: inline-block;
    vertical-align: middle;
    cursor: pointer;
    width: 80px;
    height: 40px;
    border: 4px solid #0e7318;
    background: #fff;
    padding: 5px;
    border-radius: 8px;
  }

  .btn__hamb {
    position: relative;
    display: block;
    width: 100%;
    height: 4px;
    background: rgb(115, 14, 73);
    cursor: pointer;
    div {
      width: 100%;
      height: 100%;
    }
    &:before,
    &:after {
      content: "";
      width: 100%;
      height: 100%;
      position: absolute;
      left: 0;
      background: #730e0e;
    }
    &:before {
      top: -8px;
    }
    &:after {
      top: 8px;
    }
  }
  /*Стили мобильного меню*/
  .mobile-menu {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    height: 100%;
    width: 100%;
    z-index: 100;
  }
  @media (min-width: 768px) {
    .mobile-menu {
      padding-top: 0;
    }
  }
  /*получпрозрачный фон*/
  .mobile-menu .mm__bg {
    position: absolute;
    left: 0;
    top: 0;
    width: 100%;
    height: 100%;
    background: rgba(20, 20, 20, 0.8);
    z-index: 100;
  }
  /*Контейнер мобильного меню, именно он выезжает слева*/
  .mobile-menu .mm__wrapper {
    visibility: hidden;
    -webkit-transform: translateX(-100%);
    transform: translateX(-100%);
    transition: all 0.4s ease-in-out;
    overflow-y: auto;
    position: relative;
    width: 100%;
    height: 100%;
    z-index: 200;
    touch-action: auto;
    -ms-touch-action: auto;
    background: #fff;
  }
  @media (min-width: 768px) {
    .mobile-menu .mm__wrapper {
      width: 35%;
    }
  }
  @media (min-width: 1200px) {
    .mobile-menu .mm__wrapper {
      width: 25%;
    }
  }

  .open {
    visibility: visible;
    -webkit-transform: translateX(0);
    transform: translateX(0%);
    transition: all 0.4s ease-in-out;
    overflow-y: auto;
    position: relative;
    width: 100%;
    height: 100%;
    z-index: 200;
    touch-action: auto;
    -ms-touch-action: auto;
    background: #fff;
  }

  /*Стили логотипа в меню (опционально)*/
  .mobile-menu .h__logo {
    padding-left: 40px;
    font-size: 2rem;
    font-weight: 700;
    color: #333;
    line-height: 1.25;
    margin-left: 20px;
    margin-top: 15px;
  }

  /*Стили крестика закрытия меню*/
  .mm__header .close-btn {
    position: absolute;
    top: 0;
    right: 0;
    margin-right: 15px;
    margin-top: 15px;
  }

  .close-btn {
    position: relative;
    width: 20px;
    height: 20px;
    -webkit-transform: rotate(45deg);
    -ms-transform: rotate(45deg);
    transform: rotate(45deg);
    cursor: pointer;
  }
  .close-btn:before {
    width: 2px;
    height: 18px;
    left: 8px;
    top: 0;
  }
  .close-btn:after {
    height: 2px;
    width: 18px;
    top: 8px;
    left: 0;
  }
  .close-btn:before,
  .close-btn:after {
    content: "";
    background: #000;
    position: absolute;
  }
  .close-btn--red:before,
  .close-btn--red:after {
    background: #000000;
  }
</style>
