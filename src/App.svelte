<script>
	import { fade, fly } from 'svelte/transition';
	import NavBar from './NavBar.svelte';
	import Greeting from './Greeting.svelte';
	import AboutMe from './AboutMe.svelte';
	import Contact from './Contact.svelte';
  import { onMount } from 'svelte';

	let scrollPos;
	let elementPos
	let windowHeight;
	let loaded;
	
	$: if (loaded) {
		elementPos = document.getElementById('main').getBoundingClientRect().top;
	}


	const handleResize = () => {
		document.documentElement.style.setProperty('--vh', `${windowHeight}px`);
		elementPos = document.getElementById('main').getBoundingClientRect().top;
		console.log('onResize:', (elementPos - (elementPos * .333)), elementPos)
	};

	onMount(() => {
		document.documentElement.style.setProperty('--vh', `${windowHeight}px`);		
  })

</script>

<style>
	div {
		height: var(--vh);
		width: 100vw;
	}
</style>

<svelte:window bind:scrollY={scrollPos} bind:innerHeight={windowHeight} on:resize={handleResize}/>
<div>
	<NavBar />
	<Greeting />
	<AboutMe scrollPos={scrollPos} loaded={loaded}/>
	<Contact scrollPos={scrollPos} elementPos={elementPos} windowHeight={windowHeight}/>
</div>


