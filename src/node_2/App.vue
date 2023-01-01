<script setup>
import { ref } from 'vue';
import ButtonCounter from './components/custom/ButtonCounter.vue';
import BlogPostVue from './components/custom/BlogPost.vue';
const posts = ref([{id:1, title:"Post 1", text:"Éste es el Post número 1", txtclr:"primary"},
        {id:2, title:"Post 2", text:"Éste es el Post número 2", txtclr:"secondary"},
        {id:3, title:"Post 3", text:"Éste es el Post número 3", txtclr:"warning"},
        {id:4, title:"Post 4", text:"Éste es el Post número 4", txtclr:"danger"},
        {id:5, title:"Post 5", text:"Éste es el Post número 5", txtclr:"success"},
        {id:6, title:"Post 6", text:"Éste es el Post número 6",},]);
const fav = ref('');
const changefav = (post)=>{
    fav.value=post;
}

</script>
<template>
    <div class="container">
        <h1>app {{ fav }}</h1>
        <ButtonCounter/>
        <BlogPostVue title="Post 1" text="Éste es el Post número 1" txtclr="primary" @metchangefav="changefav"/>
        <BlogPostVue title="Post 2" text="Éste es el Post número 2" txtclr="secondary" @metchangefav="changefav"/>
        <BlogPostVue title="Post 3" text="Éste es el Post número 3" txtclr="warning" @metchangefav="changefav"/>
        <BlogPostVue title="Post 4" text="Éste es el Post número 4" txtclr="danger" @metchangefav="changefav"/>
        <BlogPostVue title="Post 5" text="Éste es el Post número 5" txtclr="success" @metchangefav="changefav"/>
        <BlogPostVue title="Post 6" text="Éste es el Post número 6" @metchangefav="changefav"/>
        <h1>con V-for</h1>
        <BlogPostVue v-for="post in posts" 
        :key="post.id"
        :title="post.title" 
        :text="post.text" 
        :txtclr="post.txtclr"
        @metchangefav="changefav"/>
    </div>
</template>