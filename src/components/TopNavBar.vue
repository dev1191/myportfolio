<script setup>
import { ref } from 'vue'
import { Menu, X } from 'lucide-vue-next'
import ThemeSwitcher from './ThemeSwitcher.vue'

const isMenuOpen = ref(false)
</script>

<template>
  <header class="fixed top-0 left-0 w-full z-50 bg-background/80 backdrop-blur-md border-b border-outline-variant">
    <div class="max-w-container-max mx-auto px-margin-md h-16 flex justify-between items-center">
      <div class="font-headline-lg text-2xl font-extrabold text-primary tracking-tighter">
        DEV RAJ
      </div>

      <!-- Desktop Nav -->
      <nav class="hidden md:flex gap-margin-md">
        <a href="#home" class="font-label-mono text-primary border-b-2 border-primary pb-1">HOME</a>
        <a href="#about" class="font-label-mono text-on-surface-variant hover:text-primary transition-colors">ABOUT</a>
        <a href="#projects" class="font-label-mono text-on-surface-variant hover:text-primary transition-colors">PROJECTS</a>
        <a href="#contact" class="font-label-mono text-on-surface-variant hover:text-primary transition-colors">CONTACT</a>
      </nav>

      <div class="hidden md:flex items-center gap-base">
        <ThemeSwitcher />
        <button class="font-label-mono px-margin-sm py-2 bg-primary text-on-primary font-bold hover:opacity-80 transition-all">
         <a href="https://drive.google.com/file/d/1G4w8MCi4iNrHUdPcIzihPkGcw_TJ_1MR/view?usp=sharing">
           RESUME
         </a>
        </button>
      </div>

      <!-- Mobile Actions -->
      <div class="md:hidden flex items-center gap-margin-sm z-50">
        <ThemeSwitcher />
        <button @click="isMenuOpen = !isMenuOpen" class="text-primary p-2">
          <Menu v-if="!isMenuOpen" :size="24" />
          <X v-else :size="24" />
        </button>
      </div>

      <!-- Mobile Nav Overlay -->
      <transition
        enter-active-class="transition duration-300 ease-out"
        enter-from-class="opacity-0 translate-x-full"
        enter-to-class="opacity-100 translate-x-0"
        leave-active-class="transition duration-200 ease-in"
        leave-from-class="opacity-100 translate-x-0"
        leave-to-class="opacity-0 translate-x-full"
      >
        <div 
          v-if="isMenuOpen" 
          class="fixed inset-0 bg-background z-[60] md:hidden flex flex-col p-margin-md"
        >
          <!-- Close button in overlay -->
          <div class="flex justify-end mb-12">
            <button @click="isMenuOpen = false" class="text-primary p-2">
              <X :size="32" />
            </button>
          </div>

          <div class="flex flex-col gap-8 w-full">
            <a @click="isMenuOpen = false" href="#home" class="font-label-mono text-3xl text-primary border-b border-outline-variant pb-4">HOME</a>
            <a @click="isMenuOpen = false" href="#about" class="font-label-mono text-3xl text-on-surface-variant hover:text-primary transition-colors border-b border-outline-variant pb-4">ABOUT</a>
            <a @click="isMenuOpen = false" href="#projects" class="font-label-mono text-3xl text-on-surface-variant hover:text-primary transition-colors border-b border-outline-variant pb-4">PROJECTS</a>
            <a @click="isMenuOpen = false" href="#contact" class="font-label-mono text-3xl text-on-surface-variant hover:text-primary transition-colors border-b border-outline-variant pb-4">CONTACT</a>
            
            <button @click="isMenuOpen = false" class="mt-8 font-label-mono px-margin-md py-6 bg-primary text-on-primary font-bold tracking-widest text-lg">
              DOWNLOAD RESUME
            </button>
          </div>
        </div>
      </transition>
    </div>
  </header>
</template>
