<script>
	import { fade } from 'svelte/transition';
	import { onMount, onDestroy } from 'svelte';
    import { goto } from '$app/navigation';
	let current = 0;
	let interval;

	const slides = [
		{
			title: 'KOFFITOP Inventory System',
			desc: ' KOFFITOP Inventory System is a management tool designed for milk tea shops to track stock levels, monitor ingredient usage, and automate restocking for efficient daily operations.',
			img: '/images/KOFFITOP.png',
            link: '/works/koffitop.svelte' 
		},
		{
			title: 'FLAREPOLE Emergency Response System',
			desc: ' FlarePole is an emergency response system featuring a smart pole that, when activated, instantly alerts nearby rescuers. It’s integrated with a real-time emergency monitoring system and hotline application to ensure rapid and coordinated response during critical situations.',
			img: '/images/flarepole.png',
            link: '/works/flarepole' 
		},
		{
			title: 'JANEILANYARD Lanyard Editing System',
			desc: 'JANEILANYARD is a web-based system that combines lanyard editing software with inventory management system, making design and stock tracking easy and efficient.',
			img: '/images/Janei.png',
            link: '/works/janei' 
		},
		{
			title: 'DRIPSTR E-commerce Platform',
			desc: 'Dripstr is an integrated platform that combines e-commerce with a separate editing software, featuring artist pages where customers can commission custom artwork. It supports seamless art sales while giving artists a dedicated space to manage commissions and showcase their work.',
			img: '/images/Drips.png',
            link: '/works/dripstr'
		}
	];

	function next() {
		current = (current + 1) % slides.length;
	}

	function startAutoSlide() {
		interval = setInterval(next, 3000); // auto change
	}

	function stopAutoSlide() {
		clearInterval(interval);
	}

	onMount(() => {
		startAutoSlide();
	});

	onDestroy(() => {
		stopAutoSlide();
	});
</script>

<div class="h-full w-full">
	<!-- Slider -->
	<div
		class="relative mt-5 w-full p-10"
		on:mouseenter={stopAutoSlide}
		on:mouseleave={startAutoSlide}
	>
		<div class="flex gap-10">
			<!-- Left text -->
			<div class="w-1/2 items-center justify-center p-10">
				<div>
					<span
						class="text-shadow-[#FB09FF] text-shadow-lg stalinist-one-regular top-5 text-5xl text-white"
						>DESIGNS</span
					>
				</div>

				{#key current}
					<div class="mt-10 space-y-5 pt-10">
						<h2
							class="monomaniac-one-regular text-[clamp(0.8rem,1.5vw,1.2rem)] leading-snug text-white drop-shadow-[0_0_10px_#FB09FF]"
							in:fade={{ duration: 600 }} 
						>
							{slides[current].title}
						</h2>

						<p
							class="drop-shadow-white text-sm leading-relaxed text-gray-300 md:text-base"
							in:fade={{ duration: 600 }}
						>
							{slides[current].desc}
						</p>
                        <div class="mt-10">
                            <button
                            on:click={() => goto(slides[current].link)}
                            in:fade={{ duration: 600 }}
                                class="mt-6 rounded-lg border border-purple-400/70 bg-gradient-to-r from-purple-800/30
                       via-black to-blue-800/30
                       px-6 py-2 font-semibold text-white
                       shadow-[0_0_15px_rgba(139,92,246,0.6)]
                       transition-all duration-300
                       hover:scale-105
                       hover:border-purple-300 hover:shadow-[0_0_25px_#a855f7,0_0_50px_#6366f1]"
                            >
                                Explore More
                        </button>
                        </div>
						
					</div>
				{/key}
			</div>

			<!-- Right card stack -->
			<div class="flex w-1/2 flex-col items-center gap-4">
				<!-- Big active image -->
				{#key current}
					<div
						class="flex
                     items-center justify-center rounded-xl border
                     border-purple-400/50 bg-gradient-to-br from-purple-900
                     via-black
                     to-blue-900 p-5 shadow-[0_0_25px_rgba(139,92,246,0.8)] backdrop-blur-md"
					>
						<img
							src={slides[current].img}
							class="w-[80%] rounded-xl border border-white/20 object-cover
                       shadow-lg shadow-purple-800/70"
							in:fade={{ duration: 600 }}
						/>
					</div>
				{/key}

				<!-- Small stacked previews -->
				<div class="mt-5 flex gap-3">
					{#each slides as slide, i}
						<div
							class="transform cursor-pointer rounded-lg border
                       border-purple-400/30 bg-gradient-to-br
                       from-purple-800 via-black to-blue-900 p-2
                       shadow-[0_0_15px_rgba(139,92,246,0.6)] transition-all duration-300 hover:rotate-1
                       hover:scale-110"
							on:click={() => (current = i)}
						>
							<img
								src={slide.img}
								class="h-20 w-20 rounded-lg border border-white/10 object-cover"
							/>
						</div>
					{/each}
				</div>
			</div>
		</div>
	</div>
</div>
