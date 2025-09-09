<template>
    <section class="relative w-full" data-aos="zoom-in-up">
        <div class="absolute top-0 inset-x-0 h-64 flex items-start">
            <div class="h-24 w-2/3 bg-gradient-to-br from-[#570cac] blur-2xl invinsible opacity-40"></div>
            <div class="h-20 w-3/5 bg-gradient-to-r from[#670ccf] opacity-40 blur-2xl"></div>
        </div>
        <div class="w-full px-5 sm:px-8 md:px-12 lg:px-8 max-w-screen-lg lg:max-w-screen-xl mx-auto relative">
            <div class="grid lg:grid-cols-2 gap-10 xl:gap-14 relative pt-14 lg:max-w-none max-w-2xl md:max-w-3xl mx-auto">
                <div class="lg:py-6">
                    <div  class="text-center lg:text-left ">
                        <h1 class="pt-4 text-white font-bold text-4xl md:text-5xl lg:text-6xl">
                            Hi, I'm <span class="text-transparent bg-clip-text bg-gradient-to-r from-primary to-pink-300"> Chim</span>
                        </h1>
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

</script>