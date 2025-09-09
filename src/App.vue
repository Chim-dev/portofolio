<script setup>
// import components asynchronously
import { defineAsyncComponent } from 'vue';
import { ref, onMounted } from 'vue';

const Navbar = defineAsyncComponent(() => import('@/components/NavBar.vue'))
const HeroSection = defineAsyncComponent(() => import('@/components/HeroSection.vue'))

// Stars animation state
const starryStyle = ref('twinkling') // Options: 'twinkling', 'shooting', 'floating'

// Generate random stars data
const generateStars = (count) => {
  return Array.from({ length: count }, (_, i) => ({
    id: i,
    left: Math.random() * 100,
    top: Math.random() * 100,
    size: Math.random() * 3 + 1,
    delay: Math.random() * 5,
    duration: Math.random() * 3 + 2
  }))
}

const stars = ref(generateStars(150))
const shootingStars = ref(generateStars(8))

// Switch background styles
const switchStarStyle = (style) => {
  starryStyle.value = style
}
</script>

<template>
  <div class="relative bg-[#0a0a0a] min-h-screen overflow-hidden">
    
    <!-- Style Switcher (Remove this in production) -->
    <div class="fixed top-4 right-4 z-50 flex gap-2">
      <button 
        @click="switchStarStyle('twinkling')"
        :class="['px-3 py-1 text-xs rounded bg-white/20 text-white border transition hover:text-secondary ease-linear', starryStyle === 'twinkling' ? 'bg-white/40' : '']"
      >
        Twinkling
      </button>
      <button 
        @click="switchStarStyle('shooting')"
        :class="['px-3 py-1 text-xs rounded bg-white/20 text-white border transition hover:text-secondary ease-linear', starryStyle === 'shooting' ? 'bg-white/40' : '']"
      >
        Shooting
      </button>
      <button 
        @click="switchStarStyle('floating')"
        :class="['px-3 py-1 text-xs rounded bg-white/20 text-white border transition hover:text-secondary ease-linear', starryStyle === 'floating' ? 'bg-white/40' : '']"
      >
        Floating
      </button>
    </div>

    <!-- Background Stars Layer -->
    <div class="absolute inset-0 overflow-hidden">
      
      <!-- Twinkling Stars -->
      <div v-if="starryStyle === 'twinkling'" class="absolute inset-0">
        <div
          v-for="star in stars"
          :key="`twinkle-${star.id}`"
          class="absolute rounded-full bg-white animate-twinkle"
          :style="{
            left: star.left + '%',
            top: star.top + '%',
            width: star.size + 'px',
            height: star.size + 'px',
            animationDelay: star.delay + 's',
            animationDuration: star.duration + 's'
          }"
        ></div>
        <!-- Add some larger, brighter stars -->
        <div
          v-for="star in stars.slice(0, 20)"
          :key="`bright-${star.id}`"
          class="absolute rounded-full bg-blue-200 animate-pulse"
          :style="{
            left: (star.left + 10) % 100 + '%',
            top: (star.top + 10) % 100 + '%',
            width: (star.size + 2) + 'px',
            height: (star.size + 2) + 'px',
            animationDelay: (star.delay + 1) + 's',
            animationDuration: (star.duration + 1) + 's'
          }"
        ></div>
      </div>

      <!-- Shooting Stars -->
      <div v-if="starryStyle === 'shooting'" class="absolute inset-0">
        <!-- Static background stars -->
        <div
          v-for="star in stars"
          :key="`static-${star.id}`"
          class="absolute rounded-full bg-white opacity-60"
          :style="{
            left: star.left + '%',
            top: star.top + '%',
            width: (star.size * 0.8) + 'px',
            height: (star.size * 0.8) + 'px'
          }"
        ></div>
        <!-- Shooting stars -->
        <div
          v-for="star in shootingStars"
          :key="`shooting-${star.id}`"
          class="absolute w-1 h-1 bg-white rounded-full animate-shooting-star"
          :style="{
            left: star.left + '%',
            top: star.top + '%',
            animationDelay: star.delay + 's',
            animationDuration: (star.duration + 2) + 's'
          }"
        ></div>
      </div>

      <!-- Floating Stars -->
      <div v-if="starryStyle === 'floating'" class="absolute inset-0">
        <div
          v-for="star in stars"
          :key="`floating-${star.id}`"
          class="absolute rounded-full bg-white animate-float-star"
          :style="{
            left: star.left + '%',
            top: star.top + '%',
            width: star.size + 'px',
            height: star.size + 'px',
            animationDelay: star.delay + 's',
            animationDuration: (star.duration + 8) + 's'
          }"
        ></div>
        <!-- Add some colorful stars -->
        <div
          v-for="star in stars.slice(0, 30)"
          :key="`color-${star.id}`"
          class="absolute rounded-full animate-float-star"
          :class="[
            star.id % 4 === 0 ? 'bg-blue-300' :
            star.id % 4 === 1 ? 'bg-purple-300' :
            star.id % 4 === 2 ? 'bg-pink-300' : 'bg-yellow-300'
          ]"
          :style="{
            left: (star.left + 20) % 100 + '%',
            top: (star.top + 20) % 100 + '%',
            width: (star.size + 1) + 'px',
            height: (star.size + 1) + 'px',
            animationDelay: (star.delay + 2) + 's',
            animationDuration: (star.duration + 6) + 's'
          }"
        ></div>
      </div>

      <!-- Nebula/Galaxy effect -->
      <div class="absolute inset-0 opacity-30">
        <div class="absolute top-1/4 right-1/4 w-96 h-96 bg-gradient-to-r from-purple-900/20 to-blue-900/20 rounded-full blur-3xl"></div>
        <div class="absolute bottom-1/4 left-1/4 w-80 h-80 bg-gradient-to-r from-indigo-900/20 to-purple-900/20 rounded-full blur-3xl"></div>
      </div>
    </div>

    <!-- Main Content -->
    <div class="relative z-10">
      <Navbar/>
      <HeroSection/>
    </div>
  </div>
</template>

<style scoped>
/* Twinkling Animation */
@keyframes twinkle {
  0%, 100% { 
    opacity: 0.3; 
    transform: scale(1); 
  }
  50% { 
    opacity: 1; 
    transform: scale(1.2); 
  }
}

.animate-twinkle {
  animation: twinkle 2s ease-in-out infinite;
}

/* Shooting Star Animation */
@keyframes shooting-star {
  0% {
    transform: translateX(-100px) translateY(-100px) rotate(45deg);
    opacity: 0;
  }
  10% {
    opacity: 1;
  }
  90% {
    opacity: 1;
  }
  100% {
    transform: translateX(1000px) translateY(1000px) rotate(45deg);
    opacity: 0;
  }
}

.animate-shooting-star {
  animation: shooting-star 4s linear infinite;
}

.animate-shooting-star::before {
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  width: 50px;
  height: 1px;
  background: linear-gradient(90deg, #fff, transparent);
  transform: translateX(50px) rotateZ(45deg);
  border-radius: 50%;
  filter: drop-shadow(0px 0px 6px #699bff);
}

/* Floating Stars Animation */
@keyframes float-star {
  0%, 100% {
    transform: translateY(0px) translateX(0px) scale(1);
    opacity: 0.7;
  }
  25% {
    transform: translateY(-20px) translateX(10px) scale(1.1);
    opacity: 1;
  }
  50% {
    transform: translateY(-10px) translateX(-5px) scale(0.9);
    opacity: 0.8;
  }
  75% {
    transform: translateY(-25px) translateX(15px) scale(1.05);
    opacity: 0.9;
  }
}

.animate-float-star {
  animation: float-star 10s ease-in-out infinite;
}

/* Add a subtle glow to all stars */
.bg-white {
  box-shadow: 0 0 6px rgba(255, 255, 255, 0.8);
}

.bg-blue-200,
.bg-blue-300 {
  box-shadow: 0 0 8px rgba(147, 197, 253, 0.8);
}

.bg-purple-300 {
  box-shadow: 0 0 8px rgba(196, 181, 253, 0.8);
}

.bg-pink-300 {
  box-shadow: 0 0 8px rgba(249, 168, 212, 0.8);
}

.bg-yellow-300 {
  box-shadow: 0 0 8px rgba(253, 224, 71, 0.8);
}
</style>