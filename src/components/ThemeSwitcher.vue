<script setup>
import { Sun, Moon } from 'lucide-vue-next'
import { useTheme } from '../composables/useTheme'

const { isDark, toggleTheme } = useTheme()
</script>

<template>
  <button 
    @click="toggleTheme" 
    class="stitched-module p-2 border border-outline-variant hover:border-primary transition-all group flex items-center justify-center"
    aria-label="Toggle Theme"
  >
    <Sun v-if="isDark" class="text-primary group-hover:rotate-45 transition-transform" :size="20" />
    <Moon v-else class="text-on-surface-variant group-hover:-rotate-12 transition-transform" :size="20" />
  </button>
</template>
