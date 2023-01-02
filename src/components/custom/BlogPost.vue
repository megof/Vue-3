<script setup>
//const pro = defineProps(['title','text','txtclr'])
console.log(pro.txtclr)
const pro = defineProps({
    title: String,
    id: Number,
    body: String,
    txtclr:{
        type: String,
        default: "danger",
    },})
    const asd=(t)=>{
        console.log(t)
    }
const usemit = defineEmits(['metchangefav'])
</script>
<template>
    <div class="card" @click="usemit('metchangefav', title)">
        <div class="card-body" >
            <h5 class="card-title" :class="`text-${txtclr}`" >{{id}}: {{ title }}</h5>
            <p>{{ body }}</p>
        </div>
    </div>
</template>
