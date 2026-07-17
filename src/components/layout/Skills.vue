<template>
  <section id="skills" class="mt-32">
    <SectionHeader title="My Skills" />
    <div class="mt-20 flex justify-center">
      <ul class="flex flex-wrap justify-center items-center">
        <li ref="skillsRefs" v-for="(element, index) in skills" :key="index"
          :class="`mx-[15px] rounded-[12px] mb-7 bg-gradient-to-t ${element.bgGradient}`">
          <div class="rounded-[12px] bg-primary mt-[3px] p-12 md:p-5 text-center">
            <h3 class="font-bold text-[35px] text-white flex items-center justify-center">
              <Countup v-if="visibleItems[index]" :endVal="element.percentage" :startVal="0" :duration="2" /> %
            </h3>
            <p class="font-normal text-[16px]" :style="{ color: element.textColor }">{{ element.title }}</p>
          </div>
        </li>
      </ul>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from "vue";
import SectionHeader from "@/components/UI/SectionHeader.vue";

const skills = ref([
  {
    percentage: 95,
    title: 'HTML',
    bgGradient: 'to-[#acac39] from-[#1f1e1c99]',
    textColor: '#ffe600'
  },
  {
    percentage: 85,
    title: 'VUE',
    bgGradient: 'to-[#00a9ff99] from-[#1f1e1c99]',
    textColor: '#00a9ff'
  },
  {
    percentage: 82,
    title: 'CSS',
    bgGradient: 'to-[#ff9a0099] from-[#1f1e1c99]',
    textColor: '#ff9a00'
  },
  {
    percentage: 80,
    title: 'JavaScript',
    bgGradient: 'to-[#59c37899] from-[#1f1e1c99]',
    textColor: '#59c378'
  },
  {
    percentage: 75,
    title: 'Figma',
    bgGradient: 'to-[#acac39] from-[#1f1e1c99]',
    textColor: '#ffe600'
  },
  {
    percentage: 70,
    title: 'React',
    bgGradient: 'to-[#dd584f99] from-[#1f1e1c99]',
    textColor: '#dd584f'
  },
  {
    percentage: 50,
    title: 'C Language',
    bgGradient: 'to-[#ff9a0099] from-[#1f1e1c99]',
    textColor: '#ff9a00'
  },
  {
    percentage: 45,
    title: 'Python',
    bgGradient: 'to-[#9e00ff99] from-[#1f1e1c99]',
    textColor: '#9e00ff'
  },
  {
    percentage: 40,
    title: 'Java',
    bgGradient: 'to-[#59c37899] from-[#1f1e1c99]',
    textColor: '#59c378'
  },
  {
    percentage: 40,
    title: 'WordPress',
    bgGradient: 'to-[#00a9ff99] from-[#1f1e1c99]',
    textColor: '#00a9ff'
  },
])

// Track visibility of items
const visibleItems = ref(skills.value.map(() => false));
const skillsRefs = ref([]);

onMounted(() => {
  const observer = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        const index = skillsRefs.value.indexOf(entry.target);
        if (index !== -1) {
          if (entry.isIntersecting) {
            visibleItems.value[index] = false; // reset before triggering
            setTimeout(() => {
              visibleItems.value[index] = true; // trigger animation again
            }, 50);
          } else {
            visibleItems.value[index] = false; // reset when leaving view
          }
        }
      });
    },
    { threshold: 0.3 } // when 30% visible
  );

  skillsRefs.value.forEach((el) => observer.observe(el));
});
</script>