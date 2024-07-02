<template>
    <div class="container">
      <h2 class="display-2">Skills</h2>
      <div id="info">
          <div v-if="skills">             
              <p class="lead">{{ about[0].information[0] }}</p> 
              <p class="lead">{{ about[0].information[1] }}</p> 
              <p class="lead">{{ about[0].information[2] }}</p> 
              <p class="lead">{{ about[0].information[3] }}</p>
              <p class="lead">{{ skills.language }}</p>
          </div>
      <Spinner v-else/>
      </div>
    </div>
  </template>
  
  <script setup>
  import Spinner from './Spinner.vue'
  import {computed, onMounted } from 'vue'
  import {useStore} from 'vuex'
  
  const store = useStore()
      const skills = 
      computed(() => store.state.skills)
  
  
      onMounted(() => {
          store.dispatch('fetchAbout')
      })
  </script>

<style scoped></style>