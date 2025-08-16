<script>
	import { onMount } from 'svelte';
	import Skill from './Skill.svelte';
    import { fly } from 'svelte/transition';
	const colors = ['#9747FF', 'gray', '#5E0552'];
	let fills = ['white', 'white', 'white']; // initial fill for each svg
	let currentIndex = 0;
	let interval;

	// Function to update fills so only one svg is colored, cycling colors by index
	function updateFills() {
		fills = fills.map((_, i) => (i === currentIndex ? colors[currentIndex] : 'white'));
	}

	onMount(() => {
		updateFills();
		interval = setInterval(() => {
			currentIndex = (currentIndex + 1) % fills.length;
			updateFills();
		}, 1500);
		return () => clearInterval(interval);
	});

    let container;
	let visible = false;
	let hasScrolled = false;

	function onScroll() {
		if (!hasScrolled) {
			hasScrolled = true;
			checkVisibility();
		}
	}

	function checkVisibility() {
		if (!container) return;
		const rect = container.getBoundingClientRect();
		if (rect.top < window.innerHeight && rect.bottom > 0) {
			visible = true;
			window.removeEventListener('scroll', onScroll);
		}
	}

	onMount(() => {
		window.addEventListener('scroll', onScroll);
		// Optionally check on mount in case user reloads while scrolled down
		checkVisibility();

		return () => {
			window.removeEventListener('scroll', onScroll);
		};
	});
</script>

<div class="justify-content-center relative m-10 h-full w-full">
	
    {#if visible}
	<div in:fly={{ x: 100, duration: 1000 }}	bind:this={container} class="justify-content-center flex justify-between pb-10 pt-10">
		<div>
			<span
				class="text-shadow-[#FB09FF] text-shadow-lg stalinist-one-regular top-5 text-5xl text-white"
				data-text="SKILLS & TOOLS">SKILLS & TOOLS</span
			>
		</div>

		<div class=" flex gap-5">
			<svg width="80" height="80" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
				<polygon
					points="25 0, 72 0, 45 48, 71 100, 25 100, 0 50"
					fill={fills[0]}
					stroke="white"
					stroke-width="2"
				/>
			</svg>

			<svg
				width="80"
				height="80"
				viewBox="0 0 100 100"
				xmlns="http://www.w3.org/2000/svg"
				style="margin-left: -3rem"
			>
				<polygon
					points="25 0, 72 0, 45 48, 71 100, 25 100, 0 50"
					fill={fills[1]}
					stroke="white"
					stroke-width="2"
				/>
			</svg>

			<svg
				width="80"
				height="80"
				viewBox="0 0 100 100"
				xmlns="http://www.w3.org/2000/svg"
				style="margin-left: -3rem"
			>
				<polygon
					points="25 0, 72 0, 45 48, 71 100, 25 100, 0 50"
					fill={fills[2]}
					stroke="white"
					stroke-width="2"
				/>
			</svg>
		</div>
	</div>
    {:else}
	<!-- Placeholder to bind container before visible -->
	<div bind:this={container} style="height: 0;"></div>
{/if}

{#if visible}
	<div in:fly={{ x: 100, duration: 3000 }}	bind:this={container} class="absolute bottom-10 left-0 flex gap-5" style="transform: scaleX(-1);">
		<svg width="80" height="80" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
			<polygon
				points="25 0, 72 0, 45 48, 71 100, 25 100, 0 50"
				fill={fills[0]}
				stroke="white"
				stroke-width="2"
			/>
		</svg>

		<svg
			width="80"
			height="80"
			viewBox="0 0 100 100"
			xmlns="http://www.w3.org/2000/svg"
			style="margin-left: -3rem"
		>
			<polygon
				points="25 0, 72 0, 45 48, 71 100, 25 100, 0 50"
				fill={fills[1]}
				stroke="white"
				stroke-width="2"
			/>
		</svg>

		<svg
			width="80"
			height="80"
			viewBox="0 0 100 100"
			xmlns="http://www.w3.org/2000/svg"
			style="margin-left: -3rem"
		>
			<polygon
				points="25 0, 72 0, 45 48, 71 100, 25 100, 0 50"
				fill={fills[2]}
				stroke="white"
				stroke-width="2"
			/>
		</svg>
	</div>
    {:else}
	<!-- Placeholder to bind container before visible -->
	<div bind:this={container} style="height: 0;"></div>
{/if}


	<div
		class="mx-auto max-w-4xl rounded-3xl border-2 border-white bg-gradient-to-r from-gray-900 via-purple-900 to-black p-10 shadow-lg shadow-purple-800/50"
	>
		<div class="grid grid-cols-3 gap-8 text-center md:grid-cols-5">
			<!-- Each skill item -->
			<Skill icon="html5" label="HTML5" />
			<Skill icon="css3" label="CSS3" />

			<Skill icon="javascript" label="JavaScript" />
            <Skill icon="php" label="PHP" />
			<Skill icon="svelte" label="Svelte" />
			<Skill icon="react" label="React JS" />
            
			<Skill icon="figma" label="Figma" />

			<Skill icon="photoshop" label="Photoshop" />
			<Skill icon="davinci" label="DaVinci Resolve" />
			<Skill icon="canva" label="Canva" />
		</div>
	</div>

	<div class="absolute bottom-16 right-10 h-1 w-1/2 bg-white"></div>

	<div class="absolute bottom-16 right-10 h-1 w-1/2 bg-white"></div>
</div>

<style>
	polygon {
		transition: fill 1.3s ease;
	}
</style>
