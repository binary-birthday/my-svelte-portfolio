<script>
	import { draw, slide } from 'svelte/transition';
  import { quintOut } from 'svelte/easing';
  import { onMount } from 'svelte';

  export let scrollPos;

  let visible = false;

  onMount(() => {
    visible = true;
  })
</script>

<style>
  .navbar {
    height: 4.5rem;
    width: 100vw;
    background-color: white;
		top: 0;
		position: fixed;
		display: flex;
		align-items: center;
    justify-content: flex-end;
    z-index: 100;
	}
  
	.myName {
    height: 3.75rem;
    padding-right: .25rem;
	}
</style>

{#if visible }
<div class="navbar" in:slide="{{delay: 5000, duration: 100, easing: quintOut }}">
	{#if visible}
  <svg class="myName" viewBox="0 0 1017 163" fill="none" xmlns="http://www.w3.org/2000/svg">
    <path class="w" in:draw="{{duration: 400, delay: 5100, easing: quintOut}}" d="M2 160.001V2.375H72V160.001L36.7407 86.675L2 160.001Z" stroke="#E01E41" stroke-width="4"/>
    <path class="a1" in:draw="{{duration: 400, delay: 5200, easing: quintOut}}" d="M92 160.001L125.25 2.375L162 160.001H92Z" stroke="#E01E41" stroke-width="4"/>
    <path class="d" in:draw="{{duration: 400, delay: 5300, easing: quintOut}}" d="M182 2.37497V160.001C182 160.001 252 171.474 252 81.6865C252 -8.10056 182 2.37497 182 2.37497Z" stroke="#E01E41" stroke-width="4"/>
    <path class="e" in:draw="{{duration: 400, delay: 5400, easing: quintOut}}" d="M342 160.001H272V81.188M272 81.188V2.375H342L272 81.188ZM272 81.188H342" stroke="#E01E41" stroke-width="4"/>
    <path class="s" in:draw="{{duration: 400, delay: 5500, easing: quintOut}}" d="M449.477 2C449.477 2 414 17.2164 414 45.45C414 79.2995 465.466 76.0006 465.466 114.081C465.466 152.162 428.491 160 428.491 160M473.046 160V154.182H479V160H473.046Z" stroke="#E01E41" stroke-width="4"/> 
    <path class="m" in:draw="{{duration: 400, delay: 5600, easing: quintOut}}" d="M621 4.13416V159.02H551V4.13416L586.259 76.1853L621 4.13416Z" stroke="#E01E41" stroke-width="4"/>
    <path class="a2" in:draw="{{duration: 400, delay: 5700, easing: quintOut}}" d="M641 160L674.25 5.11475L711 160H641Z" stroke="#E01E41" stroke-width="4"/>
    <path class="r" in:draw="{{duration: 400, delay: 5800, easing: quintOut}}" d="M731 4.13443V159.02H800.947L777.5 75.6953C777.5 75.6953 799 74.715 799 32.5628C799 -9.58949 731 4.13443 731 4.13443Z" stroke="#E01E41" stroke-width="4"/>
    <path class="t" in:draw="{{duration: 400, delay: 5900, easing: quintOut}}" d="M856 160V3.15381M856 3.15381H821M856 3.15381H891" stroke="#E01E41" stroke-width="4"/>
    <path class="i" in:draw="{{duration: 400, delay: 6000, easing: quintOut}}" d="M910 2.17383V159.02" stroke="#E01E41" stroke-width="4"/>
    <path class="n" in:draw="{{duration: 400, delay: 6100, easing: quintOut}}"  d="M1015 159.02L945 2.17383V159.02H1015ZM1015 159.02V2.17383" stroke="#E01E41" stroke-width="4"/>
  </svg>
  {/if}
</div>
{/if}
