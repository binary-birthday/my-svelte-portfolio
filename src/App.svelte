<script>
	import { fade, fly } from 'svelte/transition';
	import NavBar from './NavBar.svelte';
	import Greeting from './Greeting.svelte';
	import AboutMe from './AboutMe.svelte';
	import Contact from './Contact.svelte';

	let scrollPos;

	window.addEventListener('resize', () => {
    // We execute the same script as before
    let vh = window.innerHeight * 0.01;
    document.documentElement.style.setProperty('--vh', `${vh}px`);
  });
  let vh = window.innerHeight * 0.01;
  document.documentElement.style.setProperty('--vh', `${vh}px`);

</script>

<style>



	div {
		width: 100vw;
		height: 100vh;
		height: calc(var(--vh, 1vh) * 100);
	}


</style>

<svelte:window bind:scrollY={scrollPos}/>
<div>
	<NavBar />
	<Greeting />
	<AboutMe y={scrollPos}/>
	<Contact y={scrollPos}/>
</div>


