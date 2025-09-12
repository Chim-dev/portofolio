<template>
    <section class="relative z-10 mt-20 pt-8 pb-6 border-t border-gray-200">
        <div class="text-center">
          <p class="text-gray-500 text-sm mb-2">
            © {{ currentYear }} CarteChia. All rights reserved.
          </p>
          <p class="text-gray-400 text-xs">
            | Built with Vue.js & Tailwind CSS |  
          </p>
          
          <!-- Optional: Social links or additional info -->
          <div class="flex justify-center space-x-4 mt-4">
            <a href="#" class="text-gray-400 hover:text-primary transition-colors duration-300 text-sm">
              Discord
            </a>
            <span class="text-gray-300">•</span>
            <a href="#mailto:CarteChia@gmail.com" class="text-gray-400 hover:text-primary transition-colors duration-300 text-sm">
              Email
            </a>
          </div>
        </div>
    </section>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount, computed } from "vue";
const currentYear = computed(() => new Date().getFullYear());
</script>
