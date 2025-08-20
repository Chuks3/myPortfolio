<template>
    <section class="mt-32" id="contact">
        <SectionHeader title="Contact Me" />
        <div class="py-8 lg:py-16 px-4 mx-auto max-w-screen-md">
            <form class="space-y-8">
                <div v-for="(item, index) in inputs" :key="index">
                    <Input :id="item.id" :label="item.label" :type="item.type" :placeholder="item.placeholder"
                        :rows="item.rows" />
                </div>
                <div class="flex justify-between">
                    <Button label="Send" />

                    <div class="mt-2 flex justify-center space-x-3 md:space-x-8">
                        <a href="https://www.linkedin.com/in/chukwuka-onyekamike-b8206022b"
                            class="text-gray-600 hover:text-blue-700">
                            <Icon icon="fa-brands:linkedin" style="font-size: 2rem" />
                        </a>
                        <a href="https://github.com/chuks3" class="text-gray-600 hover:text-white">
                            <Icon icon="fa-brands:github" style="font-size: 2rem" />
                        </a>
                        <a href="https://wa.me/+2349121672722" class="text-gray-600 hover:text-green-500">
                            <Icon icon="fa-brands:whatsapp" style="font-size: 2rem" />
                        </a>
                        <a href="https://www.instagram.com/onyekams/" class="text-gray-600 hover:text-orange-500">
                            <Icon icon="fa-brands:instagram" style="font-size: 2rem" />
                        </a>
                    </div>
                </div>
            </form>
        </div>
    </section>
</template>
<script setup>
import SectionHeader from "@/components/UI/SectionHeader.vue";
import Input from "@/components/UI/Input.vue";
import Button from "@/components/UI/Button.vue";
import { ref } from "vue";

const inputs = ref([
    { id: 'email', label: 'Your email', type: 'email', placeholder: 'email@example.com', rows: undefined },
    { id: 'subject', label: 'Subject', type: 'text', placeholder: 'Let me know how I can help', rows: undefined },
    { id: 'message', label: 'Message', type: 'textarea', placeholder: 'Leave a comment', rows: 6 },

])
</script>
<style></style>