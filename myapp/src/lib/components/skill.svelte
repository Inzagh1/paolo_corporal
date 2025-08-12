<script>
	export let icon;
	export let label;
</script>

<div
	class="flex cursor-pointer select-none flex-col items-center space-y-2 rounded-xl bg-gradient-to-br from-purple-900 to-pink-700 p-4
           shadow-md shadow-pink-600/40 transition-transform duration-300 hover:scale-110 hover:shadow-pink-500/70"
	title={label}
>
{#if icon === 'figma'}
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/figma/figma-original.svg" alt="Figma" class="w-14 h-14" />
{:else if icon === 'photoshop'}
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/photoshop/photoshop-line.svg" alt="Photoshop" class="w-14 h-14" />
{:else if icon === 'davinci'}
  <img src="/images/davinci.png" alt="DaVinci Resolve" class="w-14 h-14" />
{:else if icon === 'canva'}
  <img src="/images/canva.png" alt="Canva" class="w-14 h-14" />
{:else if icon === 'css3'}
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" alt="CSS3" class="w-14 h-14" />
{:else if icon === 'html5'}
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/html5/html5-original.svg" alt="HTML5" class="w-14 h-14" />
{:else if icon === 'javascript'}
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" alt="JavaScript" class="w-14 h-14" />
{:else if icon === 'svelte'}
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/svelte/svelte-original.svg" alt="Svelte" class="w-14 h-14" />
{:else if icon === 'react'}
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" alt="React" class="w-14 h-14" />
{:else if icon === 'php'}
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" alt="PHP" class="w-14 h-14" />
{:else if icon === 'firebase'}
  <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/firebase/firebase-plain.svg" alt="Firebase" class="w-14 h-14" />
{:else if icon === 'supabase'}
  <img src="https://seeklogo.com/images/S/supabase-logo-2994A10E03-seeklogo.com.png" alt="Supabase" class="w-14 h-14" />
{/if}


	<span class="font-semibold tracking-wide text-white">{label}</span>
</div>
