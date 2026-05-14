<script setup>

const year = new Date().getFullYear();

</script>


<template>
  <footer class="w-full py-margin-md px-margin-md flex flex-col md:flex-row justify-between items-center gap-base bg-surface-container-lowest border-t border-outline-variant max-w-container-max mx-auto border-x border-outline-variant">
    <div class="font-label-mono text-on-surface text-[10px]">
      © {{ year }} DEV RAJ // BUILT FOR PERFORMANCE
    </div>
    <div class="flex gap-margin-md">
      <a href="https://github.com/dev1191/" class="font-label-mono text-on-surface-variant hover:text-primary underline transition-all text-[10px]">GITHUB</a>
      <a href="https://www.linkedin.com/in/dev-raj-thapa-571645b5" class="font-label-mono text-on-surface-variant hover:text-primary underline transition-all text-[10px]">LINKEDIN</a>

    </div>
  </footer>
</template>

<style scoped>
.bg-surface-container-lowest {
  background-color: #0e0e0e;
}
</style>
