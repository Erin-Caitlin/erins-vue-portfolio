<template>
  <div class="container" testimonials>
    <div class="row">
      <h2 class="display-2" data-aos="zoom-in-down">Testimonials</h2>
    </div>
    <div id="carouselExampleIndicators" class="carousel slide" v-if="testimonials?.length">
      <div class="carousel-indicators">
        <button type="button" data-bs-target="#carouselExampleIndicators" :data-bs-slide-to="index" :class="{active: test.id == 1}" aria-current="true" :aria-label="`Slide ${test.id}`" v-for="(test, index) in testimonials" :key="test.id"></button>
      </div>
      <div class="carousel-inner" >
        <div class="carousel-item" :class="{ active: testimonial.id == 1 }" v-for="testimonial in testimonials" :key="testimonial.id">
            <div class="d-flex flex-row justify-content-center">
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
    border-radius: .5rem;
}


.card {
    /* margin: 0 2rem 3rem;
    box-shadow: 0 0.5rem 1rem rosybrown;
    background-color: rgb(208,188,177);
    height:80%;
    overflow-y: auto; */

  box-shadow: 0 0.5rem 1rem rosybrown;
  background-color: rgb(208, 188, 177);
}
</style>