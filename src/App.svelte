<script>
	import { fade, fly } from 'svelte/transition';
	import NavBar from './NavBar.svelte';
	import Greeting from './Greeting.svelte';
	import AboutMe from './AboutMe.svelte';
	import Contact from './Contact.svelte';

	let scrollPos;
	let windowHeight;
	let windowWidth;


	const handleResize = () => {
		document.documentElement.style.setProperty('--vh', `${windowHeight}px`);
		console.log(windowHeight)
	};
	
  document.documentElement.style.setProperty('--vh', `${windowHeight}px`);

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
	<AboutMe scrollPos={scrollPos}/>
	<Contact scrollPos={scrollPos} windowHeight={windowHeight}/>
</div>


