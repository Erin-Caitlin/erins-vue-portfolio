<template>
  <div class="container-fluid p-0" landing>
    <div class="row vh-100 align-items-center" page>
      <div class="col">
        <div class="animate__animated animate__fadeInTopLeft">
          <img src="https://erin-caitlin.github.io/portfolio-images/VuePortfolio/image24.jpg" alt="profile" class="img-fluid w-75 shadow rounded-top" loading="lazy"> 
        </div>
        </div>
        <div class="col">
            <div class="animate__animated animate__fadeInTopLeft" id="details">
                <h2 class="display-2">Erin Caitlin Williams</h2>
                <h4 class="display-4" v-if="jobTitle" title>{{ jobTitle[0].title }}</h4>
                <Spinner v-else/>
            </div>
            <div id="about-btn">
                <!-- <button type="button" id="about-direct"><a href="#about">About Me</a></button> -->
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
[landing] {
  background: rgb(177, 148, 148)
        url(https://erin-caitlin.github.io/portfolio-images/VuePortfolio/image26.jpg)
        no-repeat center ;
        background-size: cover;
        background-blend-mode: soft-light;
}

[page] {
  display: flex;
  justify-content: center;
  width: 95%;
}


</style>