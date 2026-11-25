<script setup>
import { ExternalLink, Code, Lock } from 'lucide-vue-next'

defineProps({
  title: String,
  tags: String,
  description: String,
  image: String,
  imageAlt: String,
  link: String,
  github: String
})
</script>

<template>
  <div class="stitched-module stitched-module-interactive flex flex-col group min-w-0">
    <div class="aspect-video w-full bg-surface-container overflow-hidden relative">
      <img 
        :src="image" 
        :alt="imageAlt"
        loading="lazy"
        class="w-full h-full object-cover grayscale opacity-75 group-hover:grayscale-0 group-hover:opacity-100 transition-all duration-700 scale-105 group-hover:scale-100"
      />
      <div class="absolute inset-0 bg-primary/10 opacity-0 group-hover:opacity-100 transition-opacity duration-300 pointer-events-none"></div>
    </div>
    <div class="p-margin-md flex-grow flex flex-col border-t border-outline-variant min-w-0">
      <div class="flex flex-wrap justify-between items-start gap-base mb-base">
        <h3 class="text-xl font-bold text-on-background uppercase tracking-tight">{{ title }}</h3>
        <span class="font-label-mono border border-primary text-primary px-2 py-1 text-[10px] break-words max-w-full">{{ tags }}</span>
      </div>
      <p class="text-on-surface-variant mb-margin-md flex-grow text-sm leading-relaxed">
        {{ description }}
      </p>
      <div class="flex flex-wrap gap-base">
        <a
          v-if="link && link !== '#'"
          :href="link"
          target="_blank"
          rel="noopener noreferrer"
          class="bg-primary text-on-primary font-label-mono px-margin-sm py-3 font-bold inline-flex items-center gap-2 hover:bg-primary/90 transition-all text-xs"
        >
          VIEW <ExternalLink :size="14" />
        </a>
        <span
          v-else
          class="border border-outline-variant text-on-surface-variant font-label-mono px-margin-sm py-3 font-bold inline-flex items-center gap-2 text-xs select-none"
        >
          <Lock :size="14" /> INTERNAL / NDA
        </span>

        <a
          v-if="github && github !== ''"
          :href="github"
          target="_blank"
          rel="noopener noreferrer"
          class="border border-outline-variant text-on-surface font-label-mono px-margin-sm py-3 font-bold inline-flex items-center gap-2 hover:border-primary transition-colors text-xs"
        >
          GITHUB <Code :size="14" />
        </a>
      </div>
    </div>
  </div>
</template>
