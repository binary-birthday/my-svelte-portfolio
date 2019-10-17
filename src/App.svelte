<script>
	import { fade, fly } from 'svelte/transition';
	import NavBar from './NavBar.svelte';
	import Greeting from './Greeting.svelte';
	import AboutMe from './AboutMe.svelte';
	import Contact from './Contact.svelte';

	let scrollPos;
	let windowHeight;
	let windowWidth;
	$: width = windowWidth;
	$: height = windowHeight;


	const handleResize = () => {
    let vh = windowHeight * 0.01;
		document.documentElement.style.setProperty('--vh', `${vh}px`);
		console.log(windowHeight)
  };
	
	let vh = windowHeight * 0.01;
  document.documentElement.style.setProperty('--vh', `${vh}px`);

</script>

<style>

</style>

<svelte:window bind:scrollY={scrollPos} bind:innerHeight={windowHeight} bind:innerWidth={windowWidth} on:resize={handleResize}/>
<div {width} {height}>
	<NavBar />
	<Greeting />
	<AboutMe scrollPos={scrollPos}/>
	<Contact scrollPos={scrollPos} windowHeight={windowHeight}/>
</div>


