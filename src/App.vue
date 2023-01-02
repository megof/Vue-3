<script setup>
import { ref } from 'vue';
import ButtonCounter from './components/custom/ButtonCounter.vue';
import BlogPostVue from './components/custom/BlogPost.vue';
import PaginatePost from './components/custom/PaginatePost.vue';
import LoadSpinner from './components/custom/LoadSpinner.vue';
const posts = ref([{id:1, title:"Post 1", body:"Éste es el Post número 1", txtclr:"primary"},
        {id:2, title:"Post 2", body:"Éste es el Post número 2", txtclr:"secondary"},
        {id:3, title:"Post 3", body:"Éste es el Post número 3", txtclr:"warning"},
        {id:4, title:"Post 4", body:"Éste es el Post número 4", txtclr:"danger"},
        {id:5, title:"Post 5", body:"Éste es el Post número 5", txtclr:"success"},
        {id:6, title:"Post 6", body:"Éste es el Post número 6",},]);
const fav = ref('');
const changefav = (post)=>{
    fav.value=post;
}


const Load = ref(true)
const postsfetch = ref([]);
fetch('https://jsonplaceholder.typicode.com/posts')
      .then(respuesta => respuesta.json())
      .then(datos => postsfetch.value = datos)
      .finally(() => (Load.value = false))
const pag = ref(0);
const btnincr = 5
const changepag = (add)=>{
    console.log(add);
    console.log(pag.value);
    pag.value+=add;
}
</script>
<template>
    <LoadSpinner v-if="Load"/>
    <div class="container" v-else>
        <ButtonCounter/>
        <h1>app {{ fav }}</h1>
        <PaginatePost class="mb-2" 
        @metchangepag="changepag"
        :block="pag"
        :incr="btnincr"
        :size="postsfetch.length"/>
        <BlogPostVue v-for="post in postsfetch.slice(pag,pag+btnincr)" 
        :key="post.id"
        :id="post.id"
        :title="post.title" 
        :body="post.body" 
        :txtclr="post.txtclr"
        @metchangepag="changepag"/>
        <BlogPostVue id=1 title="Post 1" body="Éste es el Post número 1" txtclr="primary" @metchangefav="changefav"/>
        <BlogPostVue id=2 title="Post 2" body="Éste es el Post número 2" txtclr="secondary" @metchangefav="changefav"/>
        <BlogPostVue id=3 title="Post 3" body="Éste es el Post número 3" txtclr="warning" @metchangefav="changefav"/>
        <BlogPostVue id=4 title="Post 4" body="Éste es el Post número 4" txtclr="danger" @metchangefav="changefav"/>
        <BlogPostVue id=5 title="Post 5" body="Éste es el Post número 5" txtclr="success" @metchangefav="changefav"/>
        <BlogPostVue id=6 title="Post 6" body="Éste es el Post número 6" @metchangefav="changefav"/>
        <h1>con V-for</h1>
        <BlogPostVue v-for="post in postsfetch" 
        :key="post.id"
        :id="post.id"
        :title="post.title" 
        :body="post.body" 
        :txtclr="post.txtclr"
        @metchangefav="changefav"/>
    </div>
</template>