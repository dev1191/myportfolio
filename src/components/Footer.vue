<script setup>

const year = new Date().getFullYear();

</script>


<template>
  <footer class="w-full py-margin-md px-margin-md flex flex-col md:flex-row justify-between items-center gap-base bg-surface-container border-t border-outline-variant max-w-container-max mx-auto border-x">
    <div class="font-label-mono text-on-surface text-[10px]">
      © {{ year }} DEV RAJ // BUILT FOR PERFORMANCE
    </div>
    <div class="flex gap-margin-md">
      <a
        href="https://github.com/dev1191/"
        target="_blank"
        rel="noopener noreferrer"
        class="font-label-mono text-on-surface-variant hover:text-primary underline underline-offset-4 transition-all text-[10px]"
      >
        GITHUB
      </a>
      <a
        href="https://www.linkedin.com/in/dev-raj-thapa-571645b5"
        target="_blank"
        rel="noopener noreferrer"
        class="font-label-mono text-on-surface-variant hover:text-primary underline underline-offset-4 transition-all text-[10px]"
      >
        LINKEDIN
      </a>
    </div>
  </footer>
</template>
