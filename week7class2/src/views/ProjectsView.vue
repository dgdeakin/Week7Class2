<template>
  <!-- 4th STEP: Style Binding -->
    <div :style="{fontSize: postFontSize + 'em'}">

      <!-- DISPLAY JSON FILE data in li -->
      <ol>
        <li v-for="data in datalist">
          {{ data.id }}: {{ data.title }}
        </li>
      </ol>
        This is projects page!
      <!-- Display json data here.. -->
      <!-- <ol>
        <li v-for="post in posts">{{ post.title }}</li>
      </ol> -->
      <!-- Using projectscompnent -->
      <ProjectsComponent
      v-for="post in posts"
      :key="post.id"
      :id="post.id"
      :title="post.title"
      :body="post.body" 
      @increase-size="increaseSize"
      >
      <!-- 2nd STEP:  -->

      <!-- SLOT 2nd STEP -->
      {{ post.id }}

      <!-- Value for named slot footer -->
      <template #footer>
       This is Name SLOT
      </template>

      </ProjectsComponent>

    </div>
  
</template>

<script setup>

import { ref, onMounted } from 'vue'
import ProjectsComponent from '../components/ProjectsComponent.vue'
// list to store all post items
const posts = ref([]) 

const fetchposts = async () => {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/posts")
    const data = await response.json()
    // Populate posts list with data json
    posts.value = data
  }
  catch (error)
  {
    console.error("Error fetching data..", error)
  }
}
onMounted(fetchposts)
// 3rd STEP: Create Variable and Function
const postFontSize = ref(1)

function increaseSize() {
  postFontSize.value += 1
  
}

// Local JSON file Load FIRST STEP 1
import datafile from '../data/file.json'
const datalist = ref(datafile.projects)

</script>

<style scoped>
div {
  width: 100%;
  height: 100%;
  border-style: solid;
  padding: 10px;
  
}

</style>