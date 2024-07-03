<template>
    <div class="container">
        <div class="row">
            <h2 class="display-2">Testimonials</h2>
        </div>
        <div class="row gap-2 justify-content-center" v-if="testimonials?.length">
            <Card v-for="testimonials in testimonials" :key="testimonials.id" display>
                <template #cardHeader>
                    <h4 class="card-title">{{ testimonials.name }}</h4>
                    <img :src="testimonials.img_url" :alt="testimonials.name" loading="lazy" class="img-fluid">
                    <p class="card-title">{{ testimonials.relation }}</p>
                </template>
                <template #cardBody>
                    <p class="lead">{{ testimonials.testimonial[0] }}</p>
                    <p class="lead">{{ testimonials.testimonial[1] }}</p>
                    <p class="lead">{{ testimonials.testimonial[2] }}</p>
                    <p class="lead">{{ testimonials.testimonial[3] }}</p>
                    <p class="lead">{{ testimonials.testimonial[4] }}</p>
                </template>
            </Card>
        </div>
        <Spinner v-else />
    </div>
</template>
<script>
import Card from '@/components/Card.vue';
export default {
    components: {
        Card
    },
    computed: {
        testimonials() {
            return this.$store.state.testimonials
        }
    },
    mounted() {
        this.$store.dispatch('fetchTestimonials')
    }
}
</script>

<style scoped>
[display] {
    width: 25rem;
}
</style>