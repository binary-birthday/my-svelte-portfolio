<script>
	import { fade, fly } from 'svelte/transition';
	import NavBar from './NavBar.svelte';
	import Greeting from './Greeting.svelte';
	import AboutMe from './AboutMe.svelte';
	import Contact from './Contact.svelte';
  import { onMount } from 'svelte';

	let scrollPos;
	let elementPos;
	let windowHeight;
	let height;
	let initHeight;
	
	const setVhVar = () => {
		document.documentElement.style.setProperty('--vh', `${windowHeight}px`);
	}

	const getPostion = () => {
		let newPostion = document.getElementById('form').getBoundingClientRect().top;
		console.log('getPosition fired, element postion is:', newPostion)
		return newPostion;
	}

	$: if (initHeight != height) {
		elementPos = getPostion();
	}

	const handleResize = () => {
		setVhVar()
		elementPos = getPostion();
	};

	onMount(() => {
		setVhVar();
		elementPos = getPostion();
	})
</script>

<style>
	div {
		height: var(--vh);
		height: 100vh;
		width: 100vw;
	} 
</style>

<svelte:window bind:scrollY={scrollPos} bind:innerHeight={windowHeight} on:resize={handleResize}/>
<div>
	<NavBar {scrollPos}/>
	<Greeting {scrollPos} />
	<AboutMe {scrollPos} bind:height/>
	<Contact {scrollPos} {elementPos} {windowHeight}/>
</div>


