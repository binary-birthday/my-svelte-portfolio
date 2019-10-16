<script>
	import { fade, fly } from 'svelte/transition';
	import NavBar from './NavBar.svelte';
	import Greeting from './Greeting.svelte';
	import AboutMe from './AboutMe.svelte';
	import Contact from './Contact.svelte';

	let scrollPos;
</script>

<style>



	div {
		width: 100vw;
		height: 100vh;
	}


</style>

<svelte:window bind:scrollY={scrollPos}/>
<div>
	<NavBar />
	<Greeting />
	<AboutMe y={scrollPos}/>
	<Contact y={scrollPos}/>
</div>


