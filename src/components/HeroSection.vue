<script setup>
import { Terminal, ExternalLink, ArrowDown } from 'lucide-vue-next'

const RESUME_URL = 'https://drive.google.com/file/d/1G4w8MCi4iNrHUdPcIzihPkGcw_TJ_1MR/view?usp=sharing'
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
        <span class="font-label-mono text-primary mb-base block">[ AVAILABLE FOR HIRE ]</span>
        <h1 class="text-headline-xl font-extrabold text-on-background mb-base tracking-tighter leading-none">
          DEV RAJ
        </h1>
        <p class="text-2xl sm:text-3xl lg:text-headline-lg text-on-surface-variant mb-margin-md tracking-tight">
          Backend Developer &amp; Scalable Systems Architect
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

        <!-- Hero CTAs -->
        <div class="mt-margin-md flex flex-wrap gap-base">
          <a
            :href="RESUME_URL"
            target="_blank"
            rel="noopener noreferrer"
            class="bg-primary text-on-primary font-label-mono px-margin-sm py-3.5 font-bold inline-flex items-center gap-2 hover:opacity-85 transition-all text-xs"
          >
            DOWNLOAD RESUME <ExternalLink :size="14" />
          </a>
          <a
            href="#projects"
            class="border border-outline-variant text-on-surface font-label-mono px-margin-sm py-3.5 font-bold inline-flex items-center gap-2 hover:border-primary hover:text-primary transition-colors text-xs"
          >
            VIEW PROJECTS <ArrowDown :size="14" />
          </a>
        </div>
      </div>
    </div>

    <!-- Avatar Module (visible across mobile, tablet, and desktop) -->
    <div class="stitched-module flex items-center justify-center p-margin-md sm:p-12 lg:p-16 border-t lg:border-t-0 lg:border-l border-outline-variant">
      <div 
        v-motion
        :initial="{ opacity: 0, scale: 0.9 }"
        :enter="{ opacity: 1, scale: 1 }"
        :duration="1000"
        class="relative"
      >
        <div class="w-40 h-40 sm:w-48 sm:h-48 lg:w-64 lg:h-64 border-2 border-primary p-2 overflow-hidden bg-surface-container">
          <img 
            src="/images/avatars/01JPVP9M88ZHCX6TVS7Z96P042.jpeg" 
            alt="Dev Raj Avatar"
            loading="eager"
            fetchpriority="high"
            class="w-full h-full object-cover grayscale hover:grayscale-0 transition-all duration-700"
          />
        </div>
        <!-- Decorative corner brackets -->
        <div class="absolute -top-3 -right-3 lg:-top-4 lg:-right-4 w-8 h-8 lg:w-12 lg:h-12 border-t-2 border-r-2 border-primary"></div>
        <div class="absolute -bottom-3 -left-3 lg:-bottom-4 lg:-left-4 w-8 h-8 lg:w-12 lg:h-12 border-b-2 border-l-2 border-primary"></div>
      </div>
    </div>
  </section>
</template>
