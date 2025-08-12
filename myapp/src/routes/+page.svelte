<main class="h-auto bg-[#212121] text-white flex">
	<!-- Sticky navbar (left side) -->
	<aside class="md:w-1/8  w-full md:sticky md:top-0 h-auto md:h-screen flex-shrink-0 flex flex-col items-center justify-center">
        <!-- Logo -->
        <div class="flex justify-center p-4 mt-10 md:mt-0">
            <img src="/images/logo.png" alt="Logo" class="h-24" />
        </div>
    
        <!-- Nav buttons -->
        <div class="p-10">
            <div class="border-3 rounded-4xl border-white bg-gray-300/30 flex justify-around md:flex-col md:items-center p-7 text-white text-2xl gap-16">
                <button on:click={() => scrollToSection('home')} aria-label="Home" class="cursor-pointer text-3xl">
                    <i class="fa-solid fa-house"></i>
                </button>
                <button on:click={() => scrollToSection('skills')} aria-label="Skills" class="cursor-pointer text-3xl">
                    <i class="fa-solid fa-fire"></i>
                </button>
                <button on:click={() => scrollToSection('works')} aria-label="Sample Projects" class="cursor-pointer text-3xl">
                    <i class="fa-solid fa-book"></i>
                </button>
            </div>
        </div>
    </aside>
    

	<!-- Page sections -->
	<div class="flex-1">
		<section id="home" class="flex h-screen pl-0 p-10 items-center relative justify-center">
           <Home />
        </section>

		<section id="skills" class="flex h-screen items-center justify-center">
			<h1 class="text-4xl">Skills</h1>
		</section>

		<section id="works" class="flex h-screen items-center justify-center">
			<h1 class="text-4xl">Sample Projects</h1>
		</section>
	</div>
</main>

<script>
	import Home from "$lib/components/home.svelte";

	// Smooth scroll function
	const scrollToSection = (id) => {
		document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' });
	};
</script>
