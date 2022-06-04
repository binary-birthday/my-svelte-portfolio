<script>
  import NavBar from "./NavBar.svelte";
  import Greeting from "./Greeting.svelte";
  import Contact from "./Contact.svelte";
  import { onMount } from "svelte";

  let scrollPos;
  let elementPos;
  let windowHeight;
  let height;
  let initHeight;

  const setVhVar = () => {
    document.documentElement.style.setProperty("--vh", `${windowHeight}px`);
  };

  const getPostion = () => {
    let newPostion = document
      .getElementById("form")
      .getBoundingClientRect().top;
    console.log("getPosition fired, element postion is:", newPostion);
    return newPostion;
  };

  $: if (initHeight != height) {
    elementPos = getPostion();
  }

  const handleResize = () => {
    setVhVar();
    elementPos = getPostion();
  };

  onMount(() => {
    setVhVar();
    elementPos = getPostion();
  });
</script>

<svelte:window
  bind:scrollY={scrollPos}
  bind:innerHeight={windowHeight}
  on:resize={handleResize}
/>
<div>
  <NavBar {scrollPos} />
  <Greeting {scrollPos} />
  <Contact {scrollPos} {elementPos} {windowHeight} />
</div>

<style>
  div {
    height: var(--vh);
    height: 100vh;
    width: 100vw;
  }
</style>
