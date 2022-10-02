<script>
  import { navigating } from "$app/stores";
  import Loader from "$lib/Loader.svelte";
  import { loading } from "$lib/loading";
  $: $loading = !!$navigating;
  let is_active = false;
  let toggle_active = () => {
    is_active = !is_active;
  };
</script>

{#if $loading}
  <Loader />
{/if}
<div class="outer-container">
  <div class="top-bar">
    <h3
      on:click={() => {
        if (window.location.pathname !== "/") {
          window.location.pathname = "/";
        }
      }}
      class="title"
    >
      <span class="header-bold">C.R.O.P</span>-<span class="header-bold">D</span
      >
    </h3>
    <ul class="top-menu">
      <li>&nbsp;</li>
      <li class="header-bold li-items">
        <a class="li-item" href="/dashboard">DashBoard</a>
        <a class="li-item" href="/">Usage</a>
        <a class="li-item" href="/">Working</a>
        <a class="li-item" href="/">About</a>
      </li>
    </ul>
    <ul class="top-menu-mobile">
      <li>
        <div class="hamburger" class:is_active on:click={toggle_active}>
          <div class="hamburger__container">
            <div class="hamburger__inner" />
            <div class="hamburger__hidden" />
          </div>
        </div>
      </li>
    </ul>
  </div>
  <div class="navbar-links top-menu-mobile" class:active={is_active}>
    <ul class="sub-menu" on:click={toggle_active}>
      <li><a href="/dashboard">DashBoard</a></li>
      <li><a href="/">Usage</a></li>
      <li><a href="/">Working</a></li>
      <li><a href="/">About</a></li>
      <li><a href="/" target="_blank">Github</a></li>
    </ul>
  </div>
  <slot />
</div>

<style>
  .outer-container {
    user-select: none;
  }
  .title {
    cursor: pointer;
  }
  .top-bar {
    font-family: "Major Mono Display", monospace;
  }

  .hamburger {
    position: absolute;
    top: 1.5%;
    right: 2%;
    transform: scale(0.6);
  }
  .hamburger {
    padding: 15px;
    cursor: pointer;
    display: inline-block;
    overflow: hidden;
    background-color: transparent;
  }
  .hamburger__container {
    width: 32px;
    height: 20px;
    position: relative;
  }
  .hamburger:hover .hamburger__inner {
    transform: translate(-51px, 50%);
    opacity: 0;
  }
  .hamburger:hover .hamburger__inner::before,
  .hamburger:hover .hamburger__inner::after {
    transform: translate(102px, 0);
    opacity: 0;
  }
  .hamburger.is_active .hamburger__inner {
    display: none;
  }
  .hamburger__inner {
    width: 100%;
    height: 2px;
    background-color: rgb(0, 0, 0);
    border-radius: 4px;
    position: absolute;
    transition-property: transform, opacity;
    transition-timing-function: ease;
    transition-duration: 0.4s;
    top: 50%;
    transform: translate(5px, -50%);
    opacity: 1;
  }
  .hamburger__inner::before,
  .hamburger__inner::after {
    width: 100%;
    height: 2px;
    background-color: rgb(0, 0, 0);
    border-radius: 4px;
    position: absolute;
    transition-property: transform, opacity;
    transition-timing-function: ease;
    transition-duration: 0.4s;
    content: "";
    opacity: 1;
    transform: translate(-5px, 0);
  }
  .hamburger__inner::before {
    top: -13px;
  }
  .hamburger__inner::after {
    top: 13px;
  }
  .hamburger:hover .hamburger__hidden {
    opacity: 1;
    transform: translate(0, -50%);
  }
  .hamburger:hover .hamburger__hidden::before,
  .hamburger:hover .hamburger__hidden::after {
    opacity: 1;
    transform: translate(0, 0);
  }
  .hamburger.is_active .hamburger__hidden {
    opacity: 1;
    transform: rotate(45deg);
  }
  .hamburger.is_active .hamburger__hidden::before {
    transform: translate(0, 13px) rotate(90deg);
    transform-origin: center;
  }
  .hamburger.is_active .hamburger__hidden::after {
    transform-origin: center;
    transform: translate(0, -13px) rotate(0);
  }
  .hamburger__hidden {
    opacity: 0;
    width: 100%;
    height: 2px;
    background-color: #fff;
    border-radius: 4px;
    position: absolute;
    transition-property: transform, opacity;
    transition-timing-function: ease;
    transition-duration: 0.4s;
    background-color: var(--btn-primary-color-background-color);
    top: 50%;
    transform: translate(51px, -50%);
  }
  .hamburger__hidden::before,
  .hamburger__hidden::after {
    width: 100%;
    height: 2px;
    background-color: #fff;
    border-radius: 4px;
    position: absolute;
    transition-property: transform, opacity;
    transition-timing-function: ease;
    transition-duration: 0.4s;
    background-color: var(--btn-primary-color-background-color);
    content: "";
    transform: translate(102px, 0);
  }
  .hamburger__hidden::before {
    top: -13px;
  }
  .hamburger__hidden::after {
    top: 13px;
  }

  .navbar-links ul {
    margin: 0;
    padding: 0;
    display: flex;
    position: absolute;
    text-decoration: none;
    -webkit-user-select: none; /* Chrome all / Safari all */
    -moz-user-select: none; /* Firefox all */
    -ms-user-select: none; /* IE 10+ */
    user-select: none;
    z-index: 2;
  }

  .navbar-links li {
    list-style: none;
    background-color: var(--white);
    padding: 5px 0;
    border-bottom: 2px solid whitesmoke;
  }

  .navbar-links li a {
    text-decoration: none;
    color: var(--black);
    padding: 0.1rem;
    display: block;
  }
  .navbar-links li:hover {
    background-color: var(--purple-panel);
  }
  @media (max-width: 992px) {
    .navbar-links {
      width: 100%;
      display: none;
    }

    .navbar-links ul {
      flex-direction: column;
      width: 100%;
    }

    .navbar-links li {
      text-align: center;
    }

    .navbar-links li a {
      padding: 0.5rem 1rem;
    }

    .navbar-links.active {
      display: flex;
    }
  }
</style>
