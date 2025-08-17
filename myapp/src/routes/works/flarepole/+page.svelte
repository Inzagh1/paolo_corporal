<script>
    import { fade } from 'svelte/transition';
    import { fly } from 'svelte/transition';
    import { goto } from '$app/navigation';
  
    const galleryImages = [
      "/images/flarepole/flarepole3.png",
      "/images/flarepole/flarepole1.png",
      "/images/flarepole/flarepole2.png",
      "/images/flarepole/flarepole4.png",
    ];
  
    function goBack() {
      goto('/#works');
    }
  </script>
  
  <div class="min-h-screen bg-gradient-to-br from-black via-[#0a0a12] to-[#11101a] text-white font-mono relative flex flex-col items-center p-10">
  
    <!-- Back Button -->
    <button 
      on:click={goBack}
      class="absolute z-1 top-6 cursor-pointer left-6 flex items-center gap-2 text-white bg-black/50 hover:bg-black/70 rounded-full px-4 py-2 shadow-lg transition-all duration-300 hover:scale-105"
      in:fade
    >
      <svg xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
        <path stroke-linecap="round" stroke-linejoin="round" d="M15 19l-7-7 7-7" />
      </svg>
      Back
    </button>
  
    <!-- Centered Content -->
    <div class="flex flex-col md:flex-row gap-10 w-full mt-10 md:mt-0  md:max-w-7xl items-center justify-center">
  
      <div class="w-full md:w-1/2 flex flex-col justify-center space-y-6 text-center md:text-start md:p-10">
        <h1 class="mb-6 stalinist-one-regular text-xl md:text-5xl font-bold text-transparent bg-clip-text bg-gradient-to-r from-purple-400 to-blue-500 animate-text-fade" in:fade>
            FLAREPOLE Emergency Response System
        </h1>
        <p class="max-w-3xl text-md md:text-xl leading-relaxed text-gray-300 monomaniac-one-regular tracking-wide" in:fade>
            FlarePole is an emergency response system featuring a smart pole that, when activated, instantly alerts nearby rescuers. It’s integrated with a real-time emergency monitoring system and hotline application to ensure rapid and coordinated response during critical situations.
        </p>
        <p class="max-w-3xl text-md md:text-xl leading-relaxed text-gray-300 monomaniac-one-regular tracking-wide" in:fade>
            Collaborative Design with UI/UX team members "Software app", Solo work "Mobile app".
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
    <div class="mt-16 w-full flex flex-col md:flex-row justify-center items-center gap-6">
        <div class="relative rounded-xl p-1 bg-gradient-to-r from-purple-500 via-blue-400 to-purple-500 animate-border-glow w-full md:w-[800px]">
          <iframe 
            title="Flare Pole Prototype 1"
            class="rounded-lg w-full h-[250px] md:h-[450px] bg-black"
            style="border: none;"
            src="https://embed.figma.com/proto/YKmt6Eso94lsKKPY4YU47V/FLARE-POLE-PROTOTYPE?page-id=89%3A3&node-id=198-6&viewport=-1254%2C528%2C0.26&scaling=contain&content-scaling=fixed&starting-point-node-id=198%3A6&embed-host=share" 
            allowfullscreen
          ></iframe>
        </div>
      
        <!-- Second iframe -->
        <div class="w-full md:w-[500px] relative rounded-xl p-1 bg-gradient-to-r from-purple-500 via-blue-400 to-purple-500 animate-border-glow ">
          <iframe 
            title="Flare Pole Prototype 2"
            class="rounded-lg w-full h-[450px] bg-black"
            style="border: 1px solid rgba(0, 0, 0, 0.1);"
            src="https://embed.figma.com/proto/YKmt6Eso94lsKKPY4YU47V/FLARE-POLE-PROTOTYPE?page-id=89%3A2&node-id=229-72&p=f&viewport=1367%2C259%2C0.28&scaling=scale-down&content-scaling=fixed&starting-point-node-id=229%3A52&embed-host=share" 
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
  
  