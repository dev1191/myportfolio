<script setup>
import { Sun, Moon } from 'lucide-vue-next'
import { useTheme } from '../composables/useTheme'

const { isDark, toggleTheme } = useTheme()
</script>

<template>
  <button 
    type="button"
    @click="toggleTheme" 
    class="stitched-module stitched-module-interactive p-2.5 border border-outline-variant hover:border-primary transition-all group flex items-center justify-center cursor-pointer"
    aria-label="Toggle Theme"
    :aria-pressed="isDark"
  >
    <Sun v-if="isDark" class="text-primary group-hover:rotate-45 transition-transform" :size="20" />
    <Moon v-else class="text-on-surface-variant group-hover:-rotate-12 transition-transform" :size="20" />
  </button>
</template>
