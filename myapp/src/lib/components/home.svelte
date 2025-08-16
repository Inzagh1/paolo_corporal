<script>
	import { onMount } from 'svelte';

	const titles = ['UI/UX Designer', 'FrontEnd Developer', 'Graphic Designer'];

	let idx = 0;
	let currentTitle = titles[idx];
	let isGlitch = false;

	function swapTitle() {
		isGlitch = true;
		setTimeout(() => {
			idx = (idx + 1) % titles.length;
			currentTitle = titles[idx];
			setTimeout(() => (isGlitch = false), 260);
		}, 160);
	}

	onMount(() => {
		const interval = setInterval(swapTitle, 3000);
		return () => clearInterval(interval);
	});
</script>

<div 
	class="rounded-4xl border-3  relative h-full w-full border-white bg-[url('/images/bg.png')] bg-cover bg-center"
>
	<img src="/images/pao.png" alt="picOFme" class="glitch-img h-full" />

	<!--PAO-->
	<div
		class="rounded-b-4xl border-b-3 border-l-3 border-r-3 absolute left-1/2 top-0 -mt-1 flex h-[15%] w-[30%] -translate-x-1/2 items-center justify-center rounded-tr-none border-white bg-[#212121]"
	>
		<span class="glitch-text stalinist-one-regular text-5xl text-white" data-text="PAO">PAO</span>
	</div>

	<div class="absolute border-white border-2 h-[60%] w-[30%] bg-black/60 top-5 right-5 p-5 rounded-xl rounded-b-[15%] overflow-hidden flex items-center justify-center">
        <span class="monomaniac-one-regular text-white text-[clamp(0.8rem,1.5vw,1.2rem)] leading-snug text-center">
            "UI/UX Designer and Frontend Developer focused on creating intuitive, visually appealing, and responsive digital experiences. I blend creativity with technical expertise to craft interfaces that enhance user satisfaction."
        </span>
    </div>
    

	<!--TEXT TITLE-->
	<div
		class="border-l-3 border-t-3 absolute -bottom-1 -right-1 h-1/3 w-[60%] rounded-3xl rounded-bl-none rounded-tr-none border-white bg-[#212121] pl-3 pt-3"
	>
		<div
			class="rounded-br-4xl border-3  animate-pulse shadow-lg shadow-purple-800/50 flex h-full w-full items-center justify-center rounded-tl-xl border-white bg-gradient-to-r from-[#212121] via-purple-500/50 to-pink-500/50 px-4"
		>
			<!-- Glitch effect text -->
			<span
				class="stalinist-one-regular relative inline-block text-3xl font-bold text-white"
				data-text={currentTitle}
				class:glitch={isGlitch}
			>
				{currentTitle}
			</span>
		</div>
	</div>
</div>

<style>
	span {
		letter-spacing: 0.2px;
	}
	.glitch::before,
	.glitch::after {
		content: attr(data-text);
		position: absolute;
		left: 0;
		top: 0;
		width: 100%;
		pointer-events: none;
	}

	.glitch::before {
		color: rgba(255, 0, 72, 0.85);
		transform: translate(-2px, -1px);
		clip-path: inset(0 0 50% 0);
		animation: glitch-before 240ms linear;
	}

	.glitch::after {
		color: rgba(0, 150, 255, 0.9);
		transform: translate(2px, 1px);
		clip-path: inset(50% 0 0 0);
		animation: glitch-after 300ms linear;
	}

	@keyframes glitch-before {
		0% {
			transform: translate(0, 0);
			opacity: 1;
		}
		20% {
			transform: translate(-6px, -3px) skewX(-6deg);
			opacity: 0.9;
		}
		40% {
			transform: translate(4px, -1px) skewX(3deg);
			opacity: 0.85;
		}
		60% {
			transform: translate(-3px, 2px) skewX(-2deg);
			opacity: 0.9;
		}
		80% {
			transform: translate(2px, -1px) skewX(1deg);
			opacity: 0.95;
		}
		100% {
			transform: translate(0, 0);
			opacity: 1;
		}
	}

	@keyframes glitch-after {
		0% {
			transform: translate(0, 0);
			opacity: 1;
		}
		20% {
			transform: translate(6px, 3px) skewX(6deg);
			opacity: 0.9;
		}
		40% {
			transform: translate(-4px, 1px) skewX(-3deg);
			opacity: 0.85;
		}
		60% {
			transform: translate(3px, -2px) skewX(2deg);
			opacity: 0.9;
		}
		80% {
			transform: translate(-2px, 1px) skewX(-1deg);
			opacity: 0.95;
		}
		100% {
			transform: translate(0, 0);
			opacity: 1;
		}
	}

	
</style>
