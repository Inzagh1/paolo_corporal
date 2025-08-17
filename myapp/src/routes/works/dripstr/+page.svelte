<script>
    import { fade } from 'svelte/transition';
    import { fly } from 'svelte/transition';
    import { goto } from '$app/navigation';
  
    const galleryImages = [
      "/images/dripstr/drip1.png",
      "/images/dripstr/drip2.png",
      "/images/dripstr/drip4.png",
      "/images/dripstr/drip3.png",
    ];
  
    function goBack() {
      // Navigate to main page and scroll to works section
      goto('/#works');
    }
  </script>
  
  <div class="min-h-screen bg-gradient-to-br from-black via-[#0a0a12] to-[#11101a] text-white font-mono relative flex flex-col items-center p-10">
  
    <!-- Back Button -->
    <button 
      on:click={goBack}
      class="absolute z-1 cursor-pointer top-6 left-6 flex items-center gap-2 text-white bg-black/50 hover:bg-black/70 rounded-full px-4 py-2 shadow-lg transition-all duration-300 hover:scale-105"
      in:fade
    >
      <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
        <path stroke-linecap="round" stroke-linejoin="round" d="M15 19l-7-7 7-7" />
      </svg>
      Back
    </button>
  
    <!-- Centered Content -->
    <div class="flex flex-col md:flex-row gap-10 w-full mt-10 md:mt-0 max-w-7xl items-center justify-center">
  
      <div class="md:w-1/2 w-full  flex flex-col justify-center space-y-6 text-center md:text-start md:p-10">
        <h1 class="mb-6 stalinist-one-regular text-xl md:text-5xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-purple-400 to-blue-500 animate-text-fade" in:fade>
            DRIPSTR E-commerce Platform
        </h1>
        <p class="max-w-3xl text-md md:text-xl leading-relaxed text-gray-300 monomaniac-one-regular tracking-wide" in:fade>
            Dripstr is an integrated platform that combines e-commerce with a separate editing software, featuring artist pages where customers can commission custom artwork. It supports seamless art sales while giving artists a dedicated space to manage commissions and showcase their work.
        </p>
  
      </div>
  
      <div class="md:w-1/2 grid grid-cols-2 gap-4">
        {#each galleryImages as img, i}
          <div 
            class="overflow-hidden rounded-xl shadow-lg transform hover:scale-105 transition-transform duration-300 border-2 border-transparent hover:border-purple-400/60 hover:shadow-[0_0_20px_#a855f7,0_0_40px_#6366f1] relative group"
            in:fade={{ delay: i * 100 }}
          >
            <img src={img} alt="Gallery Image" class="w-full h-auto object-cover brightness-90 group-hover:brightness-110 transition-all duration-300" />
            <div class="absolute inset-0 rounded-xl border-2 border-purple-400/20 opacity-0 group-hover:opacity-100 transition-opacity duration-300 mix-blend-screen"></div>
          </div>
        {/each}
      </div>
  
    </div>
  
    <!-- Figma Prototype iframe at the bottom -->
    <div class="mt-16 w-full flex justify-center">
      <div class="relative rounded-xl p-1 bg-gradient-to-r from-purple-500 via-blue-400 to-purple-500 animate-border-glow">
        <iframe 
          title="Dripstr E-commerce Platform Prototype"
          class="rounded-lg  h-[250px]  md:w-[800px] md:h-[450px] bg-black"
          style="border: none;"
         src="https://embed.figma.com/proto/ZlpMMrrfIOA4qMmFDZiEEc/DRIPSTR-PROTOTYPE?page-id=51%3A2&node-id=662-8545&p=f&viewport=-32%2C1248%2C0.07&scaling=contain&content-scaling=fixed&starting-point-node-id=662%3A8545&embed-host=share"
          allowfullscreen
        ></iframe>
      </div>
    </div>
    
  </div>
 
  <style>
    @keyframes text-fade {
      0%, 100% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
    }
    .animate-text-fade {
      background-size: 200% 200%;
      animation: text-fade 5s ease infinite;
    }
      @keyframes border-glow {
      0% { background-position: 0% 50%; }
      50% { background-position: 100% 50%; }
      100% { background-position: 0% 50%; }
    }
    .animate-border-glow {
      background-size: 200% 200%;
      animation: border-glow 5s linear infinite;
      box-shadow: 0 0 20px rgba(139, 92, 246, 0.6), 0 0 40px rgba(99, 102, 241, 0.5);
    }
  </style>
  
  