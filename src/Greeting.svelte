<script>
  import BeatingHeart from './BeatingHeart.svelte';
  import { onMount } from 'svelte';

  let dn1 = true;
  let dn2 = true;
  let dn3 = true

  function typewriter1(node, { speed = 75 }) {
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
			duration,
			tick: t => { setTimeout(() => {
        dn1 = false;
        const i = ~~(text.length * t);
        node.textContent = text.slice(0, i);
      }, 800)
				
			}
		};
  }

  function typewriter2(node, { speed = 75 }) {
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
			duration,
			tick: t => { setTimeout(() => {
        dn2 = false;
        const i = ~~(text.length * t);
        node.textContent = text.slice(0, i);
      }, 1800)
				
			}
    };
  }
    
  function typewriter3(node, { speed = 75 }) {
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
			duration,
			tick: t => { setTimeout(() => {
        dn3 = false;
        const i = ~~(text.length * t);
        node.textContent = text.slice(0, i);
      }, 3300)
				
			}
    };
  }

  let visible = false;
  
  onMount(() => {
    visible = true;
  })
</script>

<style>

  .landing-container {
    background-color: black;
    height: 100%;
    width: 100%;
    padding-top: 5rem;
    z-index: 2;
    display: flex;
  }
  
  .left {
    width:  20%;
  }
  .right {
    width: 80%;
    z-index: 2;
  }
	
	p {
		color: white;
		font-weight: 800;
    font-size: 5rem;
  }
  
  .dn {
    display: none;
  }
</style>
	

<div class="landing-container">
  <div class="left"></div>
  <div class="right">
    {#if visible}	
    <p class:dn={dn1} in:typewriter1 class="greting1">HELLO!</p>
	  <p class:dn={dn2} in:typewriter2 class="greting2">MY NAME IS WADE</p>
	  <p class:dn={dn3} in:typewriter3 class="greting3">I BUILD WEB APPS</p>
     {/if}
  </div>
	<BeatingHeart />
</div>
