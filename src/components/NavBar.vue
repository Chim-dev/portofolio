<template>
    <header class="flex justify-between items-center p-6 bg-opacity-50 relative z-20">
        <div class="w-[70px] h-[70px] rounded-full overflow-hidden hover:scale-125 transition-all ease-in-out">
            <img src="/src/assets/logo.png" alt="" width="90" height="100">
        </div>
        <!-- Mobile Toggle Button -->
         <div class="md:hidden z-30 ">
         <button type="button" 
         class="block focus:outline-none"
         @click="isMenuOpen = !isMenuOpen"
         >
            <span v-if="isMenuOpen"  class="text-5xl">
                <img src="https://img.icons8.com/ios-filled/100/ffffff/delete-sign.png" alt="close" width="50" height="50">
            </span>
            <span v-else class="text-5xl">
                <img src="https://img.icons8.com/ios-filled/100/ffffff/menu--v6.png" alt="menu" width="50" height="50">
            </span>
         </button>
        </div>
         <!-- Navbar Link -->
         <nav
         :class="['fixed inset-0 z-20 flex flex-col items-center justify-center bg-[#1C1C1C] md:relative md:bg-transparent md:flex md:justify-between md:flex-row',
            isMenuOpen ? 'block':'hidden'
         ]"
         >
            <ul  class="flex flex-col items-center space-y-5 md:flex-row md:space-x-5 md:space-y-0">
                <li v-for="item in Menu" :key="item.name">
                    <a 
                        :href="item.href" 
                        class="flex items-center gap-2 text-white transition hover:text-secondary ease-linear text-2xl md:text-lg"
                        @click="scrollToSection(item.href)" :target="item.href.startsWith('http') ? '_blank' : null"
                         :rel="item.href.startsWith('http') ? 'noopener noreferrer' : null"
                    >
                        <!-- Display SVG icon if item has one -->
                        <span v-if="item.icon" v-html="item.icon" class="w-6 h-6 md:w-5 md:h-5"></span>
                        {{ item.name }}
                    </a>
                </li>
            </ul>
         </nav>
    </header>
</template>

<script setup>
import { ref } from 'vue';

// GitHub SVG icon
const githubIcon = `<svg viewBox="0 0 24 24" fill="currentColor" xmlns="http://www.w3.org/2000/svg">
    <path d="M12 0.297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/>
</svg>`;

// Alternative icons you can use
const linkIcon = `<svg viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" xmlns="http://www.w3.org/2000/svg">
    <path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"/>
    <path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"/>
</svg>`;

const Menu = ref([
    {name:'Services', href:'#services'},
    {name:'Skills', href:'#skills'},
    {name:'Projects', href:'#projects'},
    {name:'', href:'https://github.com/Chim-dev', icon: githubIcon}, // Added icon property
]);

const isMenuOpen = ref(false)

const scrollToSection = (href) => {
    isMenuOpen.value = false;
    const section = document.querySelector(href);
    if(section) {
        section.scrollIntoView({behavior : 'smooth'}); // Fixed: scrollIntoView instead of scrollToSection
    }   
}
</script>