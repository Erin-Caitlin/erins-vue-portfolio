<template>
  <div class="container" id="landing">
    <div class="row vh-100 align-items-center">
        <div class="col"><img src="https://erin-caitlin.github.io/portfolio-images/VuePortfolio/image24.jpg" alt="profile" class="img-fluid w-75 shadow rounded-top" loading="lazy"></div>
        <div class="col">
            <div id="details">
                <h1 class="display-1">Erin Caitlin Williams</h1>
                <p v-if="jobTitle" class="lead">{{ jobTitle[0].title }}</p>
                <Spinner v-else/>
            </div>
            <div id="about-btn">
                <button type="button" id="about-direct"><a href="#about">About Me</a></button>
            </div>
        </div>
    </div>
  </div>
</template>
  
  <script setup>
import Spinner from './Spinner.vue'
import {computed, onMounted} from 'vue'
import {useStore} from 'vuex'
const store = useStore()
    const jobTitle = computed(() => store.state.jobTitle)

    onMounted(() => {
        store.dispatch('fetchJobTitle')
    })
</script>
<style>
</style>