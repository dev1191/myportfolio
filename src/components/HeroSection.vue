<script setup>
import { Terminal } from 'lucide-vue-next'
</script>

<template>
  <section id="home" class="stitched-grid grid-cols-1 lg:grid-cols-3 border-b border-outline-variant">
    <!-- Hero Text -->
    <div class="stitched-module p-margin-md lg:p-16 lg:col-span-2">
      <div 
        v-motion
        :initial="{ opacity: 0, y: 20 }"
        :enter="{ opacity: 1, y: 0 }"
        :duration="800"
      >
        <span class="font-label-mono text-primary mb-base block">[ SYSTEM_INIT ]</span>
        <h1 class="text-headline-xl font-extrabold text-on-background mb-base tracking-tighter leading-none">
          DEV RAJ
        </h1>
        <p class="text-headline-lg text-on-surface-variant mb-margin-md tracking-tight">
          Backend Developer & Scalable Systems Architect
        </p>

        <div class="stitched-module border border-outline-variant p-margin-md max-w-3xl">
          <div class="flex justify-between mb-base">
            <span class="font-label-mono text-on-surface-variant">00 // OVERVIEW</span>
            <Terminal class="text-primary" :size="20" />
          </div>
          <p class="text-body-md text-on-surface leading-relaxed">
            A Backend Developer who enjoys working with Laravel, NodeJS, and Vue. Passionate about building scalable and efficient systems, solving complex problems, and continuously learning new technologies. I thrive in collaborative environments and take pride in writing clean, maintainable code that drives seamless user experiences.
          </p>
        </div>
      </div>
    </div>

    <!-- Avatar Module -->
    <div class="stitched-module hidden lg:flex items-center justify-center p-16 border-l border-outline-variant">
      <div 
        v-motion
        :initial="{ opacity: 0, scale: 0.9 }"
        :enter="{ opacity: 1, scale: 1 }"
        :duration="1000"
        class="relative"
      >
        <div class="w-64 h-64 border-2 border-primary p-2 overflow-hidden bg-surface-container">
          <img 
            src="/images/avatars/01JPVP9M88ZHCX6TVS7Z96P042.png" 
            alt="Dev Raj Avatar"
            class="w-full h-full object-cover grayscale hover:grayscale-0 transition-all duration-700"
          />
        </div>
        <!-- Decorative elements -->
        <div class="absolute -top-4 -right-4 w-12 h-12 border-t-2 border-r-2 border-primary"></div>
        <div class="absolute -bottom-4 -left-4 w-12 h-12 border-b-2 border-l-2 border-primary"></div>
      </div>
    </div>
  </section>
</template>
