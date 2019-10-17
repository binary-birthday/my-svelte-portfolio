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


	const handleResize = () => {
		document.documentElement.style.setProperty('--vh', `${windowHeight}px`);
		elementPos = document.getElementById('main').getBoundingClientRect().top;
		console.log('onResize:', elementPos)
	};

	onMount(() => {
		document.documentElement.style.setProperty('--vh', `${windowHeight}px`);
		elementPos = document.getElementById('main').getBoundingClientRect().top;	
		console.log('onMount:', elementPos)
		
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
	<AboutMe scrollPos={scrollPos} />
	<Contact scrollPos={scrollPos} elementPos={elementPos}/>
</div>


