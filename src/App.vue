<script setup>

import {ref} from 'vue'

import ButtonCounter from './components/ButtonCounter.vue'
import BlogPost from  './components/BlogPost.vue'
import PaginatePost from  './components/PaginatePost.vue'

const posts = ref([])
const postXpage = 10
const inicio = ref(0)
const fin = ref(postXpage)

const favorito = ref("");


const cambiarFavorito =(title) => { 
  favorito.value = title;
}

fetch('https://jsonplaceholder.typicode.com/posts')
  .then(res => res.json())
  .then((data) => {
    posts.value = data;
  });
</script>

<template>
  <div class="container">
    <h1>APP</h1>
    <h2>Mis Post Favoritos: {{ favorito }} </h2>


  <PaginatePost class="mb-2"/>    

    <BlogPost 
        v-for="post in posts.slice(inicio,fin)" 
        :key="post.id"
        :title="post.title" 
        :id="post.id" 
        :body="post.body" 
        :cambiarFavorito ="cambiarFavorito"
        class="mb-2"
      ></BlogPost>
    </div>
</template>