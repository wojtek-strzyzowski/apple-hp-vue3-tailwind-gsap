<script setup>
import { ref } from 'vue';
import { appleImg, searchImg, bagImg} from '../utils';
import { navLists} from '../constants';

const navItems = ref(navLists); // Verwenden Sie ref, um die Liste reaktiv zu machen

</script>

<template>

    <header class="w-full py-5 sm:px-10 px-5 flex justify-between items-center">
        <nav class="flex w-full screen-max-width">
            <img :src="appleImg" alt="Apple Image" width="14" height="18">
            <div class="flex flex-1 justify-center max-sm:hidden">
                <div v-for="(item, index) in navItems" :key="index"
                class="px-5 text-sm cursor-pointer text-gray hover:text-white transition-all">
                    {{ item }}
                </div>
            </div>
            <div class="flex items-baseline gap-7 max-sm:justify-end max-sm:flex-1">
                <img :src="searchImg" alt="Search Image" width="18" height="18">
                <img :src="bagImg" alt="Bag Image" width="18" height="18">
            </div>
        </nav>
    </header>

</template>

<style scoped>

</style>