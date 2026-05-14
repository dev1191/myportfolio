<script setup>
const skills = [
  { name: 'LARAVEL', icon: '/images/01J4G2EC993JCB66D9HXEFDJ3P.svg' },
  { name: 'NODEJS', icon: '/images/01J4KKHYKQFSC1KMH95XY9Y7ER.svg' },
  { name: 'VUE', icon: '/images/01J4G2DQ9HG46E0BED778P1J5S.svg' },
  { name: 'MYSQL', icon: '/images/01J4K97QSQ4A61B3EARQ3SJCRF.svg' },
  { name: 'MONGODB', icon: '/images/01J4K99TGE75XHG77X7FE34MEB.svg' },
  { name: 'TAILWINDCSS', icon: '/images/01J4KRYM47AD9TWEBGGXTWYVBM.svg' },
  { name: 'AWS', icon: '/images/01J4G2NP57JJDGGD9XZTAC1VVB.svg' },
  { name: 'PHP', icon: '/images/01J4G1XEB1ZNPN9ETTHKJDS4B5.png' },
]
</script>

<template>
  <section id="about" class="stitched-grid border-b border-outline-variant grid-cols-1 md:grid-cols-4">
    <!-- Expertise Block -->
    <div class="stitched-module p-margin-md md:col-span-2 md:row-span-8 md:border-r border-outline-variant flex flex-col">
      <div class="flex justify-between items-start mb-12">
        <h2 class="text-headline-lg font-bold text-primary">TECH STACK</h2>
        <span class="font-label-mono text-on-surface-variant">01 // CORE</span>
      </div>
      <p class="text-body-md text-on-background mb-margin-md">
        Specialized in architecting high-performance backends using Laravel and Node.js. Expertise in microservices, real-time data processing with Redis, and building scalable API ecosystems.
      </p>
      <div class="grid grid-cols-2 gap-base mt-auto">
        <div class="p-base border border-outline-variant">
          <p class="font-label-mono text-primary text-xl mb-1">7+</p>
          <p class="font-label-mono text-[10px] text-on-surface-variant">YEARS EXP</p>
        </div>
        <div class="p-base border border-outline-variant">
          <p class="font-label-mono text-primary text-xl mb-1">15+</p>
          <p class="font-label-mono text-[10px] text-on-surface-variant">LIVE SYSTEMS</p>
        </div>
      </div>
    </div>

    <!-- Small Tech Cells -->
    <div v-for="skill in skills" :key="skill.name" class="stitched-module p-margin-md flex flex-col items-center justify-center text-center gap-4 group">
      <img 
        :src="skill.icon" 
        :alt="skill.name"
        class="w-12 h-12 object-contain grayscale opacity-70 transition-all group-hover:grayscale-0 group-hover:opacity-100"
      />
      <span class="font-label-mono text-on-surface">{{ skill.name }}</span>
    </div>
  </section>
</template>
