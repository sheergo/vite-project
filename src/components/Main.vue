
<template>

  <input type="search" name="Search" id="" v-model="Search">
   <p>Found {{ articleCount }} articles</p>
  <div v-for="(article , index) in filteredArticles" :key="index" class="article">
    <div class="title">
      <h2>
        {{ article.title }}
      </h2>
    </div>
  {{ article.content }}
  </div>
 

</template>
<script setup>
import Articles from '../assets/Articlejson.json'
import { ref, computed } from 'vue'

const Search = ref("")

const filteredArticles = computed(() => {
  return Articles.articles.filter(article => 
    article.content.toLowerCase().includes(Search.value.toLowerCase())
  )
})

const articleCount = computed(() => filteredArticles.value.length)
</script>



<style scoped>

.article{
  width: 100%;
  height: fit-content;
  min-height: 50px;
  padding: 5px;
  background-color: lightblue;
  border: 1px solid black;
  margin-top: 2%;

}
.title{
  font-weight: bold;
}
</style>
