<script>
	import { onMount } from 'svelte';
	import Skill from './Skill.svelte';
	import { fly, fade } from 'svelte/transition';
  
	const colors = ['#9747FF', 'gray', '#5E0552'];
	let fills = ['white', 'white', 'white'];
	let currentIndex = 0;
	let interval;
  
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
  
	function checkVisibility() {
	  if (!container) return;
	  const rect = container.getBoundingClientRect();
	  if (rect.top < window.innerHeight && rect.bottom > 0) {
		visible = true;
		window.removeEventListener('scroll', checkVisibility);
	  }
	}
  
	onMount(() => {
	  window.addEventListener('scroll', checkVisibility);
	  checkVisibility();
	  return () => window.removeEventListener('scroll', checkVisibility);
	});
  </script>
  
  <div bind:this={container} class="relative m-5 h-full w-full">
	{#if visible}
	<div in:fly={{ x: 100, duration: 1000 }} class="flex flex-col md:flex-row justify-between pb-10 pt-10 items-center md:items-start">
	  <div class="mb-6 md:mb-0 text-center md:text-left">
		<span class="text-shadow-[#FB09FF] text-shadow-lg stalinist-one-regular text-3xl sm:text-4xl md:text-5xl text-white">
		  SKILLS & TOOLS
		</span>
	  </div>
  
	  <div class="flex gap-2 md:gap-4 flex-wrap justify-center md:justify-start">
		{#each fills as fill, i}
		  <svg class="w-16 h-16 sm:w-20 sm:h-20 md:w-20 md:h-20" viewBox="0 0 100 100" xmlns="http://www.w3.org/2000/svg">
			<polygon
			  points="25 0, 72 0, 45 48, 71 100, 25 100, 0 50"
			  fill={fill}
			  stroke="white"
			  stroke-width="2"
			  in:fade={{ duration: 800, delay: i * 200 }}
			/>
		  </svg>
		{/each}
	  </div>
	</div>
  {/if}
  
  
	<div class="mx-auto max-w-4xl rounded-3xl border-2 border-white bg-gradient-to-r from-gray-900 via-purple-900 to-black p-5 md:p-10 shadow-lg shadow-purple-800/50">
	  <div class="grid grid-cols-2 gap-4 md:gap-8 text-center md:grid-cols-5">
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
	{#if visible}
	<!-- Bottom mirrored arrows -->
	<div in:fly={{ x: -100, duration: 2000 }} class="hidden md:flex justify-between pb-10 pt-10 transform -scale-x-[-1]">
	  
  
	  <div class="flex gap-1">
		{#each fills as fill, i}
		  <svg width="80" height="80" viewBox="0 0 100 100" class="transform scale-x-[-1]">
			<polygon
			  points="25 0, 72 0, 45 48, 71 100, 25 100, 0 50"
			  fill={fill}
			  stroke="white"
			  stroke-width="2"
			  in:fade={{ duration: 800, delay: i * 200 }}
			/>
		  </svg>
		{/each}
	  </div>
	</div>
	{/if}
	<div class="md:absolute mt-10 bottom-16 right-10 h-1 w-full md:w-1/2 
    bg-white 
    drop-shadow-[0_0_15px_#00faff] 
    drop-shadow-[0_0_30px_#00faff] 
    drop-shadow-[0_0_60px_#00faff] 
    rounded-full">
</div>

  </div>
  
  <style>
	polygon {
	  transition: fill 1.3s ease;
	}
  </style>
  