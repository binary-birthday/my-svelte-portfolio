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
    font-style: oblique;
    transform: scale(1.02);
    color: #0E79B2;
  }

  .right {
    width: 100%;
    height: 50%;
    z-index: 10;
    padding-left: 3rem;
  }
	
	span {
		color: white;
    font-family: 'Oswald', sans-serif;
		font-weight: 600;
    font-size: calc(8vh + 8*(90vw - 400px)/ 400);
  }

  @media only screen and (max-width: 700px) {
    .landing-container {
      height: 110%;
    }
   span {
      font-size: calc(8.5vh + 8*(90vw - 400px)/ 400);
    }
    .strong {
    color: #0E79B2;
    text-shadow: .5px .5px #00000022;
  }

  }


</style>
	
<div bind:offsetHeight={height} class="landing-container">
  {#if visible}	
  <div class="right">
    <span in:typewriter="{{delay: 1200, speed: 50}}" >Hi, my name is</span><br>
	  <span in:typewriter="{{delay: 2000, speed: 50}}" class="strong">Wade Martin.</span><br>
	  <span in:typewriter="{{delay: 3000, speed: 50}}" >I build webapps.</span><br>
	  <span in:typewriter="{{delay: 4200, speed: 50}}" >Welcome to my</span><br>
	  <span in:typewriter="{{delay: 5000, speed: 50}}" >portfolio!</span><br>
  </div>
  <BeatingHeart />
  {/if}
</div>