<script setup>
import { ref, watch, nextTick, onMounted, onUnmounted } from 'vue'
import { Menu, X } from 'lucide-vue-next'
import ThemeSwitcher from './ThemeSwitcher.vue'

const RESUME_URL = 'https://drive.google.com/file/d/1U6kdHxN5oQuXApMvzlbgVjzGWdR2hWJf/view'

const navItems = [
  { id: 'home', label: 'HOME', href: '#home' },
  { id: 'about', label: 'STACK', href: '#about' },
  { id: 'projects', label: 'PROJECTS', href: '#projects' },
  { id: 'experience', label: 'EXPERIENCE', href: '#experience' },
  { id: 'contact', label: 'CONTACT', href: '#contact' }
]

const isMenuOpen = ref(false)
const activeSection = ref('home')
const menuTriggerRef = ref(null)
const closeBtnRef = ref(null)

let observer = null

watch(isMenuOpen, async (open) => {
  await nextTick()
  if (open) {
    closeBtnRef.value?.focus({ preventScroll: true })
  } else {
    menuTriggerRef.value?.focus({ preventScroll: true })
  }
})

function handleKeydown(event) {
  if (event.key === 'Escape' && isMenuOpen.value) {
    isMenuOpen.value = false
  }
}

onMounted(() => {
  window.addEventListener('keydown', handleKeydown)

  const sections = navItems
    .map((item) => document.getElementById(item.id))
    .filter(Boolean)

  if (!sections.length || typeof IntersectionObserver === 'undefined') return

  observer = new IntersectionObserver(
    (entries) => {
      const visible = entries
        .filter((entry) => entry.isIntersecting)
        .sort((a, b) => b.intersectionRatio - a.intersectionRatio)

      if (visible.length > 0) {
        activeSection.value = visible[0].target.id
      }
    },
    {
      rootMargin: '-20% 0px -55% 0px',
      threshold: [0.1, 0.25, 0.5]
    }
  )

  sections.forEach((section) => observer.observe(section))
})

onUnmounted(() => {
  window.removeEventListener('keydown', handleKeydown)
  if (observer) {
    observer.disconnect()
    observer = null
  }
})
</script>

<template>
  <header class="fixed top-0 left-0 w-full z-50 bg-background/80 backdrop-blur-md border-b border-outline-variant">
    <div class="max-w-container-max mx-auto px-margin-md h-16 flex justify-between items-center">
      <a href="#home" class="text-2xl font-extrabold text-primary tracking-tighter">
        DEV RAJ
      </a>

      <!-- Desktop Nav -->
      <nav aria-label="Primary navigation" class="hidden md:flex gap-margin-md">
        <a
          v-for="item in navItems"
          :key="item.id"
          :href="item.href"
          :aria-current="activeSection === item.id ? 'location' : undefined"
          :class="[
            'font-label-mono transition-colors pb-1',
            activeSection === item.id
              ? 'text-primary border-b-2 border-primary'
              : 'text-on-surface-variant hover:text-primary'
          ]"
        >
          {{ item.label }}
        </a>
      </nav>

      <div class="hidden md:flex items-center gap-base">
        <ThemeSwitcher />
        <a
          :href="RESUME_URL"
          target="_blank"
          rel="noopener noreferrer"
          class="font-label-mono px-margin-sm py-2 bg-primary text-on-primary font-bold hover:opacity-80 transition-all inline-flex items-center"
        >
          RESUME
        </a>
      </div>

      <!-- Mobile Actions -->
      <div class="md:hidden flex items-center gap-margin-sm z-50">
        <ThemeSwitcher />
        <button
          ref="menuTriggerRef"
          type="button"
          :aria-label="isMenuOpen ? 'Close navigation menu' : 'Open navigation menu'"
          :aria-expanded="isMenuOpen"
          aria-controls="mobile-nav-overlay"
          @click="isMenuOpen = !isMenuOpen"
          class="text-primary p-2.5"
        >
          <Menu v-if="!isMenuOpen" :size="24" />
          <X v-else :size="24" />
        </button>
      </div>
    </div>
  </header>

  <!-- Mobile Nav Overlay (teleported to body to escape header's backdrop-blur containing block) -->
  <Teleport to="body">
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
        id="mobile-nav-overlay"
        role="dialog"
        aria-modal="true"
        aria-label="Mobile navigation"
        class="fixed inset-0 bg-background z-[60] md:hidden flex flex-col p-margin-md overflow-y-auto"
      >
        <!-- Close button in overlay -->
        <div class="flex justify-end mb-12">
          <button
            ref="closeBtnRef"
            type="button"
            aria-label="Close navigation menu"
            @click="isMenuOpen = false"
            class="text-primary p-2.5"
          >
            <X :size="32" />
          </button>
        </div>

        <nav aria-label="Mobile navigation links" class="flex flex-col gap-8 w-full">
          <a
            v-for="item in navItems"
            :key="item.id"
            :href="item.href"
            :aria-current="activeSection === item.id ? 'location' : undefined"
            @click="isMenuOpen = false"
            :class="[
              'font-label-mono text-3xl border-b border-outline-variant pb-4 transition-colors',
              activeSection === item.id
                ? 'text-primary'
                : 'text-on-surface-variant hover:text-primary'
            ]"
          >
            {{ item.label }}
          </a>
          
          <a
            :href="RESUME_URL"
            target="_blank"
            rel="noopener noreferrer"
            @click="isMenuOpen = false"
            class="mt-8 font-label-mono px-margin-md py-6 bg-primary text-on-primary font-bold tracking-widest text-lg text-center block hover:opacity-90 transition-all"
          >
            DOWNLOAD RESUME
          </a>
        </nav>
      </div>
    </transition>
  </Teleport>
</template>
