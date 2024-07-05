<template>
  <div class="container">
    <div class="row">
      <h2 class="display-2">Testimonials</h2>
    </div>
    <div id="carouselExampleIndicators" class="carousel slide ikumi" v-if="testimonials?.length">
      <div class="carousel-indicators">
        <button type="button" data-bs-target="#carouselExampleIndicators" :data-bs-slide-to="index" :class="{active: test.id == 1}" aria-current="true" :aria-label="`Slide ${test.id}`" v-for="(test, index) in testimonials" :key="test.id"></button>
      </div>
      <div class="carousel-inner" >
        <div class="carousel-item" :class="{ active: testimonial.id == 1 }" v-for="testimonial in testimonials" :key="testimonial.id">
          <Card display>
            <template #cardHeader>
              <h4 class="card-title">{{ testimonial.name }}</h4>
              <img :src="testimonial.img_url" :alt="testimonial.name" loading="lazy" class="img-fluid"/>
              <p class="card-title">{{ testimonial.relation }}</p>
            </template>
            <template #cardBody>
              <p class="lead">{{ testimonial.testimonial[0] }}</p>
              <p class="lead">{{ testimonial.testimonial[1] }}</p>
              <p class="lead">{{ testimonial.testimonial[2] }}</p>
              <p class="lead">{{ testimonial.testimonial[3] }}</p>
              <p class="lead">{{ testimonial.testimonial[4] }}</p>
            </template>
          </Card>
        </div>
        
        <button class="carousel-control-prev" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="prev">
          <span class="carousel-control-prev-icon" aria-hidden="true"></span>
          <span class="visually-hidden">Previous</span>
        </button>
        <button class="carousel-control-next" type="button" data-bs-target="#carouselExampleIndicators" data-bs-slide="next">
          <span class="carousel-control-next-icon" aria-hidden="true"></span>
          <span class="visually-hidden">Next</span>
        </button>
      </div>
    </div>
    <Spinner v-else />
  </div>
</template>
<script>
import Card from "@/components/Card.vue";
import Spinner from './Spinner.vue'
export default {
  components: {
    Card,
    Spinner
  },
  computed: {
    testimonials() {
      return this.$store.state.testimonials;
    },
  },
  mounted() {
    this.$store.dispatch("fetchTestimonials");
  },
};
</script>

<style scoped>
[display] {
  width: 75%;
}


.img-fluid {
    width: 10rem;
}
/* .ikumi{
    margin: 0, 0 ,0 , 10vw;
} */


</style>