<script setup>
import { ExternalLink, Code } from 'lucide-vue-next'

defineProps({
  title: String,
  tags: String,
  description: String,
  image: String,
  imageAlt: String,
  link: String,
  github:String
})
</script>

<template>
  <div class="stitched-module flex flex-col group">
    <div class="aspect-video w-full bg-surface-container overflow-hidden relative">
      <img 
        :src="image" 
        :alt="imageAlt"
        class="w-full h-full object-cover grayscale opacity-50 group-hover:grayscale-0 group-hover:opacity-100 transition-all duration-700 scale-105 group-hover:scale-100"
      />
      <div class="absolute inset-0 bg-primary/10 opacity-0 group-hover:opacity-100 transition-opacity duration-300 pointer-events-none"></div>
    </div>
    <div class="p-margin-md flex-grow flex flex-col border-t border-outline-variant">
      <div class="flex justify-between items-start mb-base">
        <h3 class="text-xl font-bold text-on-background uppercase tracking-tight">{{ title }}</h3>
        <span class="font-label-mono border border-primary text-primary px-2 py-1 text-[10px]">{{ tags }}</span>
      </div>
      <p class="text-on-surface-variant mb-margin-md flex-grow text-sm leading-relaxed">
        {{ description }}
      </p>
      <div class="flex gap-base">
        <button class="bg-primary text-on-primary font-label-mono px-margin-sm py-3 font-bold flex items-center gap-2 hover:bg-primary/90 transition-all text-xs">
        <a :href="link" target="_blank">
 VIEW  <ExternalLink :size="14" />
        </a> 
        </button>
        <button v-if="github != ''" class="border border-outline-variant text-on-surface font-label-mono px-margin-sm py-3 font-bold flex items-center gap-2 hover:border-primary transition-colors text-xs">
          GITHUB <Code :size="14" />
        </button>
      </div>
    </div>
  </div>
</template>
