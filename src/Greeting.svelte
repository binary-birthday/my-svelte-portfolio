<script>
  import BeatingHeart from './BeatingHeart.svelte';
  import { onMount } from 'svelte';
  import { fly, fade } from 'svelte/transition';
  import { quintOut } from 'svelte/easing';

  export let scrollPos;

  let height;

  $: if(scrollPos >= (height * .4)) {
    visible = false;
  }

  $: if(scrollPos < (height * .4)) {
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
    visible = !visible;
  })

</script>

<style>

  .landing-container {
    height: 110%;
    width: 100%;
    z-index: 2;
    display: flex;
    justify-content: center;
  }

  .strong {
    font-weight: 100;
    transform: scale(1.02);
    color: #0E79B2;
  }

  .left {
    width: 70%;
    height: 80%;
    padding-top: 4rem;
    z-index: 10;
  }
	
	span {
		color: white;
    font-family: 'Oswald', sans-serif;
    font-weight: 100;
    font-size: calc(7.5vh + 8*(90vw - 400px)/ 400);
  }

  @media only screen and (max-width: 700px) {
    .landing-container {
      height: 110%;
    }
    .left {
      width: 80%;
    }
    span {
      font-size: calc(6.5vh + 8*(90vw - 400px)/ 400);
    }
    .strong {
    text-shadow: .5px .5px #00000022;
    }

  }
  
</style>
	
<div bind:offsetHeight={height} class="landing-container">
  {#if visible}	
  <div class="left" out:fade="{{delay: 0, duration: 4000}}" >
    <span in:typewriter="{{delay: 700, speed: 50}}" >Hello,&nbsp</span>
    <span in:typewriter="{{delay: 1800, speed: 50}}" >my name is</span><br>
	  <span in:typewriter="{{delay: 2350, speed: 50}}" class="strong">Wade Martin.</span><br>
	  <span in:typewriter="{{delay: 3900, speed: 50}}" >I build Web Apps.</span><br>
	  <span in:typewriter="{{delay: 5700, speed: 50}}" >Welcome to my portfolio!</span>
  </div>
  <BeatingHeart />
  {/if}
</div>