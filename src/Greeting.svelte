<script>
  import BeatingHeart from './BeatingHeart.svelte';
  import { onMount } from 'svelte';
  import { fly } from 'svelte/transition';
  import { quintOut } from 'svelte/easing'

  let visible = false;

  function typewriter(node, { delay = 100, speed = 50 }) {
		const valid = (
			node.childNodes.length === 1 &&
			node.childNodes[0].nodeType === 3
		);

		if (!valid) {
			throw new Error(`This transition only works on elements with a single text node child`);
		}

		const text = node.textContent;
    const duration = text.length * speed;

		return {
      delay,
      duration,

			tick: t => {
				const i = ~~(text.length * t);
        node.textContent = text.slice(0, i);
      }

		};
  };

  onMount(() => {
    visible = true;
  })
</script>

<style>

  .landing-container {
    background-color: black;
    height: 105%;
    width: 100%;
    padding-top: 4rem;
    z-index: 2;
    display: flex;
    justify-content: flex-end;
  }

  .right {
    width: 100%;
    height: 50%;
    z-index: 10;
    padding-left: 3rem;
  }
	
	p {
		color: white;
		font-weight: 800;
    font-size: calc(12.75vmin + 8*(90vw - 400px)/ 400);
  }


</style>
	
<div class="landing-container">
  <div class="right">
    {#if visible}	
    <p in:typewriter="{{delay: 1200, speed: 50}}" class="greting1">HELLO!</p>
	  <p in:typewriter="{{delay: 2000, speed: 50}}" class="greting2">MY NAME IS WADE</p>
	  <p in:typewriter="{{delay: 3000, speed: 50}}" class="greting3">I BUILD WEB APPS</p>
    {/if}
  </div>
  <BeatingHeart />
</div>