<script setup>
import { ref } from 'vue';

const counter = ref(0);
const incremet = () => counter.value++;
</script>
<template>
    <button @click="incremet">Counter {{ counter }}</button>
</template>