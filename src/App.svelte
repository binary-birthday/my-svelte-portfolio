<script>
	import { fade, fly } from 'svelte/transition';
	import NavBar from './NavBar.svelte';
	import Greeting from './Greeting.svelte';
	import AboutMe from './AboutMe.svelte';
	import Contact from './Contact.svelte';
</script>

<style>



	div {
		width: 100vw;
		height: 100vh;
	}


</style>


<div>
	<NavBar />
	<Greeting />
	<AboutMe />
	<Contact />
</div>


