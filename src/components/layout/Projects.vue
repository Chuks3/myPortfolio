<template>
    <section id="projects" class="relative w-11/12 px-16 mx-auto">
        <SectionHeader title="My Projects" />

        <!-- Custom Navigation Button -->
        <button
            class="swiper-prev absolute top-2/3 left-4 transform -translate-y-1/2 z-10 text-white dark:bg-secondary bg-primary p-4 rounded-full">
            <Icon icon="line-md:arrow-left" class="font-bold text-3xl" />
        </button>
        <button
            class="swiper-next absolute top-2/3 right-4 transform -translate-y-1/2 z-10 text-white dark:bg-secondary bg-primary p-4 rounded-full">
            <Icon icon="line-md:arrow-right" class="font-bold text-3xl" />
        </button>

        <swiper :effect="`coverflow`" grabCursor centeredSlides :slidesPerView="`auto`"
            :coverflowEffect="{ rotate: 50, stretch: 0, depth: 100, modifier: 1, slideShadows: true, }"
            :navigation="navigationOptions" loop pagination :modules="[EffectCoverflow, Navigation]"
            class="mx-w-full mt-32">
            <swiper-slide class="max-w-[300px]" v-for="(project, index) in projects" :key="index">
                <ProjectCard :title="project.title" :description="project.description"
                    :image="getImageUrl(project.image)" :tags="project.tags" :liveLink="project.liveLink"
                    :codeLink="project.codeLink" />
            </swiper-slide>
        </swiper>
    </section>
</template>

<script setup>
import SectionHeader from "@/components/UI/SectionHeader.vue";
import ProjectCard from "@/components/UI/ProjectCard.vue";
import { Swiper, SwiperSlide } from 'swiper/vue';
import { EffectCoverflow, Navigation } from 'swiper/modules';
import { ref } from "vue";
import 'swiper/css';
import 'swiper/css/effect-coverflow';
import 'swiper/css/navigation';
import 'swiper/css/pagination';

// Define Navigation Options
const navigationOptions = {
    prevEl: '.swiper-prev',
    nextEl: '.swiper-next',
};

// This tells Vite how to find the image relative to the current file
const getImageUrl = (path) => {
  return new URL(`../../assets/images/${path}`, import.meta.url).href;
};

const projects = ref([
    {
        title: 'MICROSOFT',
        description: 'A clone of the Microsoft homepage.',
        image: 'microsoft.png',
        tags: ['HTML', 'CSS'],
        liveLink: 'https://chuks3.github.io/microsoftClone/',
        codeLink: 'https://github.com/Chuks3/microsoftClone',
    },
    {
        title: 'MOVIE LIST',
        description: 'This is a project movie site using https://www.themoviedb.org/ as an API.',
        image: 'movieList.png',
        tags: ['HTML', 'CSS', 'REACT'],
        liveLink: 'https://movie-list-dun-ten.vercel.app/',
        codeLink: 'https://github.com/Chuks3/movieList',
    },
    {
        title: 'MY PORTOFOLIO',
        description: 'This is a portfolio page.',
        image: 'portfolio.png',
        tags: ['VUE', 'HTML', 'TAILWIND', 'CSS'],
        liveLink: 'https://chukwuka-zeta.vercel.app/',
        codeLink: 'https://github.com/Chuks3/myPortfolio',
    },
    {
        title: 'CBT INTERFACE',
        description: 'This is a CBT (Computer Based Test) project that grades the user.',
        image: 'cbt.png',
        tags: ['HTML', 'CSS', 'VUE'],
        liveLink: 'https://cbt-interface.vercel.app/',
        codeLink: 'https://github.com/Chuks3/cbt-interface',
    },
    {
        title: 'ONLINE STORE',
        description: 'This is a demo project of an ecommerce store using dummy.json as an API.',
        image: 'onlineStore.png',
        tags: ['HTML', 'CSS', 'VUE', 'JavaScript'],
        liveLink: 'https://chuks-store.netlify.app/',
        codeLink: 'https://github.com/Chuks3/online-store',
    },
    {
        title: 'NINJA BIKES',
        description: 'This is a design of a catalog for sport bikes sold from Kawasaki company',
        image: 'ninja.png',
        tags: ['FIGMA'],
        liveLink: 'https://www.figma.com/proto/zJVDCIDF7NPZdsarNLSz1o?node-id=0-1&t=xyNrpOoOdfb9XHMx-6',
        codeLink: '#',
    },
    {
        title: 'TO-DO LIST',
        description: 'A simple To-Do project to keep track of your daily tasks.',
        image: 'toDoList.png',
        tags: ['HTML', 'CSS', 'JavaScript'],
        liveLink: 'https://chuks3.github.io/toDoList/',
        codeLink: 'https://github.com/Chuks3/toDoList',
    },
    {
        title: 'CHAT BOT',
        description: 'A mini AI project created to keep users company with questions and prompts.',
        image: 'chatBot.png',
        tags: ['HTML', 'CSS', 'JavaScript'],
        liveLink: 'https://chuks3.github.io/chatBot/',
        codeLink: 'https://github.com/Chuks3/chatBot',
    },
    {
        title: 'FAKE STORE',
        description: 'A demo online store using fake store api database.',
        image: 'fakeStore.png',
        tags: ['HTML', 'CSS', 'VUE'],
        liveLink: 'https://fake-store-gold-psi.vercel.app/',
        codeLink: 'https://github.com/Chuks3/fake-store',
    },
    {
        title: 'PROMPT EARN',
        description: 'An affiliate group that gives you valuable products and make it easy for you to get paid promoting them from anywhere in the world.',
        image: 'promptEarn.png',
        tags: ['HTML', 'CSS', 'VUE'],
        liveLink: 'https://promptearn.netlify.app/',
        codeLink: 'https://github.com/Chuks3/fake-store',
    },
])
</script>

<style>
.swiper-button-prev,
.swiper-button-next {
    cursor: pointer;
}

.swiper-slide {
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>