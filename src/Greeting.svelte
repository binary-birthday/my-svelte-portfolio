<script>
  import BeatingHeart from './BeatingHeart.svelte';
  import { onMount } from 'svelte';
  import { fly } from 'svelte/transition';
  import { quintOut } from 'svelte/easing'

  export let scrollPos;

  let height;

  $: if(scrollPos >= (height * .45)) {
    visible = false;
  }

  $: if(scrollPos < 100) {
    visible = true;
  }

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
    height: 125%;
    width: 100%;
    padding-top: 4rem;
    z-index: 2;
    display: flex;
    justify-content: flex-end;
  }

  .strong {
    font-weight: 100;
    transform: scale(1.01);
  }

  .right {
    width: 100%;
    height: 50%;
    z-index: 10;
    padding-left: 3rem;
  }
	
	p {
		color: white;
    font-family: 'Oswald', sans-serif;
		font-weight: 600;
    font-size: calc(8vmin + 8*(90vw - 400px)/ 400);
  }

  @media only screen and (max-width: 700px) {
    .landing-container {
      height: 110%;
    }
    p {
      font-size: calc(7vh + 8*(90vw - 400px)/ 400);
    }
  }


</style>
	
<div bind:offsetHeight={height} class="landing-container">
  {#if visible}	
  <div class="right">
    <p in:typewriter="{{delay: 1200, speed: 50}}" >Hi, my name is</p>
	  <p in:typewriter="{{delay: 2000, speed: 50}}" class="strong">Wade Martin.</p>
	  <p in:typewriter="{{delay: 3000, speed: 50}}" >I build webapps. </p>
	  <p in:typewriter="{{delay: 4000, speed: 50}}" >Welcome to my</p>
	  <p in:typewriter="{{delay: 4800, speed: 50}}" >portfolio!</p>
  </div>
  <BeatingHeart />
  {/if}
</div>