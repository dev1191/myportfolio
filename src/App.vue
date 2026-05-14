<script setup>
import TopNavBar from './components/TopNavBar.vue'
import HeroSection from './components/HeroSection.vue'
import TechStack from './components/TechStack.vue'
import ProjectGallery from './components/ProjectGallery.vue'
import ExperienceTimeline from './components/ExperienceTimeline.vue'
import ContactSection from './components/ContactSection.vue'
import Footer from './components/Footer.vue'
</script>

<template>
  <div class="min-h-screen bg-background selection:bg-primary selection:text-on-primary">
    <TopNavBar />
    
    <main class="pt-16 max-w-container-max mx-auto border-x border-outline-variant">
      <HeroSection />
      <TechStack />
      <ProjectGallery />
      <ExperienceTimeline />
      <ContactSection />
    </main>

    <Footer />
  </div>
</template>

<style>
/* Global resets if needed */
body {
  @apply antialiased;
}
</style>
