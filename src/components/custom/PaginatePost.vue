<script setup>
const pro = defineProps({
    block: Number,
    incr: Number,
    size: Number
})
const usemit = defineEmits(['metchangepag'])
</script>
<template>
    <div class="btn-group" role="group" aria-label="Baseic ecample">
        <button type="button" @click="usemit('metchangepag',-incr)" class="btn btn-danger" :disabled="block<=0">Previus</button>
        <button type="button" @click="usemit('metchangepag',incr)" class="btn btn-success" :disabled="block>=(size-incr)">Next</button>
    </div>
</template>