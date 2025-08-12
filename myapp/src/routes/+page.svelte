<script>
	import Home from '$lib/components/home.svelte';
	import Skills from '$lib/components/skills.svelte';
	import { fade } from 'svelte/transition';
	import { onMount } from 'svelte';

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

<main class="flex h-auto bg-[#212121] text-white">
	<!-- Sticky navbar (left side) -->
	<aside
		class="md:w-1/8 flex h-auto w-full flex-shrink-0 flex-col items-center justify-center md:sticky md:top-0 md:h-screen"
	>
		<!-- Logo -->
		<div class="mt-10 flex justify-center p-4 md:mt-0">
			<img src="/images/logo.png" alt="Logo" class="h-24" />
		</div>

		<!-- Nav buttons -->
		<div class="p-10">
			<div
				class="border-3 rounded-4xl flex justify-around gap-16 border-white bg-gray-300/30 p-7 text-2xl text-white md:flex-col md:items-center"
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
     
		<section
			id="home"
			class="relative flex h-screen items-center justify-center p-5 pl-0"

		>
           {#if showHome}
        <div class="h-screen w-full p-10" in:fade={{ duration: 800 }}>
            <Home />
        </div>
        {/if}
		</section>
		

		<section id="skills" class="flex h-screen items-center justify-center">
			<Skills />
		</section>

		<section id="works" class="flex h-screen items-center justify-center">
			<h1 class="text-4xl">Sample Projects</h1>
		</section>
	</div>
</main>
