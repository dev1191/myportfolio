<script setup>
import { ref } from 'vue'
import { Link, Terminal, ArrowRight } from 'lucide-vue-next'

const form = ref({
  name: '',
  email: '',
  message: ''
})
</script>

<template>
  <section id="contact" class="stitched-grid grid-cols-1 md:grid-cols-2">
    <!-- Links Column -->
    <div class="stitched-module p-margin-md md:border-r border-outline-variant">
      <div class="mb-12">
        <h2 class="text-headline-lg font-bold text-on-background mb-base tracking-tight">CONNECT</h2>
        <p class="text-body-md text-on-surface-variant leading-relaxed">
          Ready to architect your next high-performance system? Let's discuss technical specifications.
        </p>
      </div>
      <div class="space-y-margin-sm">
        <a href="https://www.linkedin.com/in/dev-raj-thapa-571645b5" target="_blank" class="flex items-center justify-between group p-base border border-outline-variant hover:border-primary transition-all">
          <div class="flex items-center gap-margin-sm">
            <Link class="text-primary" :size="18" />
            <span class="font-label-mono text-xs">LINKEDIN</span>
          </div>
          <ArrowRight class="text-on-surface-variant group-hover:text-primary transition-colors" :size="18" />
        </a>
        <a href="https://github.com/dev1191/" target="_blank" class="flex items-center justify-between group p-base border border-outline-variant hover:border-primary transition-all">
          <div class="flex items-center gap-margin-sm">
            <Terminal class="text-primary" :size="18" />
            <span class="font-label-mono text-xs">GITHUB</span>
          </div>
          <ArrowRight class="text-on-surface-variant group-hover:text-primary transition-colors" :size="18" />
        </a>
      </div>
    </div>

    <!-- Form Column -->
    <div class="stitched-module p-margin-md">
      <form @submit.prevent class="space-y-6">
        <div class="grid grid-cols-1 sm:grid-cols-2 gap-base">
          <div class="space-y-2">
            <label class="font-label-mono text-on-surface-variant text-[10px]">NAME</label>
            <input 
              v-model="form.name"
              type="text" 
              placeholder="USER_NAME"
              class="w-full bg-surface-container border border-outline-variant text-on-surface p-base focus:border-primary focus:ring-0 outline-none placeholder:text-surface-variant font-jetbrains text-sm"
            />
          </div>
          <div class="space-y-2">
            <label class="font-label-mono text-on-surface-variant text-[10px]">EMAIL</label>
            <input 
              v-model="form.email"
              type="email" 
              placeholder="USER_AUTH_MAIL"
              class="w-full bg-surface-container border border-outline-variant text-on-surface p-base focus:border-primary focus:ring-0 outline-none placeholder:text-surface-variant font-jetbrains text-sm"
            />
          </div>
        </div>
        <div class="space-y-2">
          <label class="font-label-mono text-on-surface-variant text-[10px]">MESSAGE</label>
          <textarea 
            v-model="form.message"
            rows="4" 
            placeholder="SYSTEM_QUERY_DESCRIPTION"
            class="w-full bg-surface-container border border-outline-variant text-on-surface p-base focus:border-primary focus:ring-0 outline-none placeholder:text-surface-variant font-jetbrains text-sm resize-none"
          ></textarea>
        </div>
        <button class="w-full bg-primary text-on-primary font-label-mono py-margin-sm font-bold uppercase hover:opacity-90 transition-all text-xs">
          EXECUTE_SEND
        </button>
      </form>
    </div>
  </section>
</template>
