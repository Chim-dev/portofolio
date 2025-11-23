<template>
    <section class="text-white mt-18" id="about">
        <div class="absolute z-0 top-[93rem] inset-x-0 h-64 flex items-start">
            <div class="h-24 w-64 bg-gradient-to-br from-primary via-secondary blur-2xl to-[#570cac] opacity-20"></div>
        </div>

        <div class="md:grid md:grid-cols-2 gap-8 item-center py-8 px-4 xl:gap-16 sm:py-16 xl:px-16 z-1">

            <!-- LEFT SIDE - EDUCATION -->
            <div data-aos="flip-right">
                <h2 class="text-4xl font-bold text-white text-left mb-8">My Education</h2>

                <div class="space-y-8 py-8">
                    <div 
                        v-for="element in education" 
                        :key="element.id"
                        class="flex items-center md:w-[80%] w-full rounded-xl bg-transparent shadow-lg border-2 border-white hover:bg-white/10 hover:shadow-white/50 hover:shadow-sm transition-all duration-300"
                    >
                        <div class="w-1/4">
                            <img src="/src/assets/Logo_ITK_White.png.webp" alt="logo">
                        </div>

                        <div class="w-3/4 pl-4">
                            <h3 class="text-2xl font-semibold uppercase text-transparent bg-clip-text bg-gradient-to-r from-primary to-secondary lg:text-xl">
                                {{ element.School }}
                            </h3>
                            <p class="text-white">{{ element.programs }}</p>
                            <p class="text-white">{{ element.year }}</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- RIGHT SIDE - MODERN INFO LINES -->
            <div class="mt-4 md:mt-0 text-left flex flex-col z-10 h-full" data-aos="flip-right">
                <h2 class="text-4xl font-bold text-white md:text-center text-left mb-8">
                    More <span class="text-transparent bg-clip-text bg-gradient-to-r from-[#9d50bb] to-[#6e48aa]">About</span> Me
                </h2>

                <div class="mt-6 space-y-6">

                    <div 
                        v-for="row in portfolio" 
                        :key="row.category"
                        class="pb-4 border-b border-white/20 hover:border-white/40 transition duration-300"
                    >
                        <p class="text-sm uppercase tracking-wide text-white/60">{{ row.category }}</p>
                        <p class="text-xl font-medium text-white mt-1">{{ row.value }}</p>
                    </div>

                </div>
            </div>

        </div>
    </section>
</template>

<script setup>
import { ref } from 'vue'

// LEFT
const education = ref([
    {
        id: 11231048,
        School: 'Institute Technology of Kalimantan',
        programs: 'Informatika',
        year: '2023'
    }
])

// RIGHT - MODERN INFO LINES
const portfolio = ref([
    { category: 'Name', value: 'Muhammad Abdurrachim' },
    { category: 'Major', value: 'Informatika' },
    { category: 'Skill', value: 'Full Stack Web Developer' },
    { category: 'Interest', value: 'Machine Learning, Large Language Model' }
])
</script>
