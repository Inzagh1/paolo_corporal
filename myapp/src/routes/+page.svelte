<script>
	import Home from '$lib/components/home.svelte';
	import Skills from '$lib/components/skills.svelte';
	import { fade } from 'svelte/transition';
	import { onMount } from 'svelte';
	import Designs from '$lib/components/designs.svelte';

	// Smooth scroll function
	const scrollToSection = (id) => {
		document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' });
	};

	let showHome = false;

	onMount(() => {
		setTimeout(() => {
			showHome = true;
		}, 10); // small delay to trigger fade
	});
</script>

<main class="h-auto bg-gradient-to-br from-black via-[#0a0a12] to-[#11101a] text-white md:flex">
	<!-- Sticky navbar (left side) -->
	<aside
		class="md:w-1/8 flex h-auto w-full flex-shrink-0 flex-col items-center justify-center md:sticky md:top-0 md:h-screen"
	>
		<!-- Logo -->
		<div class="mt-2 flex justify-center p-2 md:mt-10 md:p-4">
			<img src="/images/logo.png" alt="Logo" class="h-16 animate-pulse md:h-24" />
		</div>

		<!-- Nav buttons -->
		<div class="hidden p-10 md:flex">
			<div
				class="rounded-4xl before:rounded-4xl animate-bg-fade relative flex justify-around gap-16 border border-white/100 bg-black/30
					 p-7 text-2xl text-white
				
					 before:absolute before:inset-0 before:-z-10 before:bg-gradient-to-r before:from-purple-500 before:via-blue-400 before:to-pink-500 before:opacity-30 before:blur-xl md:flex-col md:items-center"
			>
				<button
					on:click={() => scrollToSection('home')}
					aria-label="Home"
					class="cursor-pointer text-3xl transition-colors hover:text-[#9747FF]"
				>
					<i class="fa-solid fa-house"></i>
				</button>
				<button
					on:click={() => scrollToSection('skills')}
					aria-label="Skills"
					class="cursor-pointer text-3xl transition-colors hover:text-[#9747FF]"
				>
					<i class="fa-solid fa-fire"></i>
				</button>
				<button
					on:click={() => scrollToSection('works')}
					aria-label="Sample Projects"
					class="cursor-pointer text-3xl transition-colors hover:text-[#9747FF]"
				>
					<i class="fa-solid fa-book"></i>
				</button>
			</div>
		</div>
	</aside>

	<!-- Page sections -->
	<div class="flex-1">
		<section id="home" class="relative flex h-screen items-center justify-center pl-0 md:p-5">
			{#if showHome}
				<div class="h-screen w-full p-4 pt-0 md:p-10" in:fade={{ duration: 800 }}>
					<Home />
				</div>
			{/if}
		</section>

		<section id="skills" class="flex h-auto items-center md:pl-10 md:pr-10 justify-center">
			<Skills />
		</section>

		<section id="works" class="relative flex h-auto overflow-hidden">
			<div class="relative flex w-full">
				<Designs />
			</div>
		</section>
	</div>
</main>

<style>
	@keyframes bg-fade {
		0%,
		100% {
			background-position: 0% 10%;
		}
		50% {
			background-position: 10% 50%;
		}
	}
	.animate-bg-fade {
		background-size: 10% 10%;
		animation: bg-fade 8s ease infinite;
	}
</style>
