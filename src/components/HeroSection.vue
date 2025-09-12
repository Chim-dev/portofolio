<template>
  <section class="relative w-full" data-aos="zoom-in-up">
    <!-- background gradient atas -->
    <div class="absolute top-0 inset-x-0 h-64 flex items-start">
      <div class="h-24 w-2/3 bg-gradient-to-br from-[#F5F5F5] blur-2xl invisible opacity-40"></div>
      <div class="h-20 w-3/5 bg-gradient-to-r from-[#fad6b8] opacity-40 blur-2xl"></div>
    </div>

    <div class="w-full px-5 sm:px-8 md:px-12 lg:px-8 max-w-screen-lg lg:max-w-screen-xl mx-auto relative">
      <!-- grid 2 kolom -->
      <div class="grid lg:grid-cols-2 gap-10 xl:gap-14 relative pt-14 lg:max-w-none max-w-2xl md:max-w-3xl mx-auto">
        
        <!-- Kolom kiri: teks -->
        <div class="lg:py-6 flex flex-col justify-center">
          <div class="text-center lg:text-left">
            <h1 class="pt-4 text-black font-bold text-4xl md:text-5xl lg:text-6xl">
              <span class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-gray-700">
                CarteChia
              </span>
            </h1>
          </div>
          <p class="text-gray-300 pt-8 text-center lg:text-left mx-auto max-w-xl text-6md">
            Hi! I'm Chim — I'm an undergraduate 
            <span class="text-transparent bg-clip-text bg-gradient-to-l from-gray-500 to-blue-500">
              Computer Science
            </span>
            student from 
            <a
              class="text-transparent bg-clip-text bg-gradient-to-r from-red-500 to-blue-300"
              href="https://itk.ac.id/" target="_blank">
              Institut Teknologi Kalimantan
            </a>,
            I'm an aspiring Full-Stack Software Engineer with a passion for building scalable and user-friendly
            applications. This website showcases my project documentation, from early experiments to more polished works,
            reflecting my growth and learning journey.
            <br>
            I love <span class="text-transparent bg-clip-text bg-gradient-to-r from-pink-100 to-orange-200">Cuteness</span>, especially from game characters as you may notice from this Website's theme.
          </p>
        </div>

        <!-- Kolom kanan: gambar -->
        <div class="flex justify-center items-center relative">
          <!-- background glow -->
          <div class="absolute z-0 w-[80%] h-[80%] bg-gradient-to-tr from-[#868585] to-[#2E2E2E] blur-2xl rounded-full"></div>
          
          <!-- gambar -->
          <div class="relative z-10 p-2 rounded-full shadow-lg border border-primary bg-white">
            <transition name="crossfade" mode="out-in">
              <img
                :key="currentImage"
                :src="currentImage"
                alt="carte"
                loading="lazy"
                class="w-64 h-64 md:w-80 md:h-80 lg:w-96 lg:h-96 rounded-full object-cover"
              />
            </transition>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>


<script setup>
import Aos from 'aos';
import 'aos/dist/aos';
Aos.init();

import { ref, onMounted, onBeforeUnmount, computed } from "vue";

// Daftar gambar (isi dengan file lokal / url sesuai kebutuhan)
const images = [
  "/src/assets/download.png",
  "/src/assets/carte1 (1).png",
  "/src/assets/carte1 (2).png",
  "/src/assets/carte aset (1).png",
  "/src/assets/carte aset (2).png",
];

const index = ref(0);
const currentImage = ref(images[index.value]);
const currentYear = computed(() => new Date().getFullYear());
let intervalId = null;

onMounted(() => {
  intervalId = setInterval(() => {
    index.value = (index.value + 1) % images.length;
    currentImage.value = images[index.value];
  }, 5000); 
});

onBeforeUnmount(() => {
  if (intervalId) {
    clearInterval(intervalId);
  }
});
</script>

<style scoped>
.crossfade-enter-active,
.crossfade-leave-active {
  transition: opacity 0.8s ease-in-out;
}

.crossfade-enter-from,
.crossfade-leave-to {
  opacity: 0;
}

.crossfade-enter-to,
.crossfade-leave-from {
  opacity: 1;
}

/* Alternative approach for smoother crossfade */
.crossfade-enter-active {
  transition: opacity 0.8s ease-in-out;
  transition-delay: 0.1s;
}

.crossfade-leave-active {
  transition: opacity 0.8s ease-in-out;
}
</style>