<script>
    import { fade } from 'svelte/transition';
  </script>
  
  <div class="min-h-screen bg-gradient-to-br from-black via-[#1a1a2e] to-[#212121] text-white p-10">
    <h1 class="text-4xl font-bold mb-6" in:fade>KOFFITOP Inventory System</h1>
    <p class="max-w-3xl text-lg leading-relaxed" in:fade>
      KOFFITOP Inventory System is a management tool designed for milk tea shops
      to track stock levels, monitor ingredient usage, and automate restocking
      for efficient daily operations.
    </p>
    <img src="/images/KOFFITOP.png" alt="Koffitop preview" class="mt-10 rounded-xl shadow-lg" in:fade />
  </div>
  