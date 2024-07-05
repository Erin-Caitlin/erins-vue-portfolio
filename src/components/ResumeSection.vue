<template>
    <div class="container" resume-page>
        <div class="row">
            <h2 class="display-2">Resume</h2>
        </div>
        <div class="row" resume>
        <div class="row gap-2 justify-content-center" v-if="education?.length" data-aos="fade-up"
        data-aos-duration="2000">
            <Card v-for="education in education" :key="education.id" cards>
                <template #cardHeader>
                    <h4 class="card-title">{{ education.school }}</h4>
                </template>
                <template #cardBody>
                    <img :src="education.img_url" :alt="education.school" loading="lazy" class="img-fluid">
                    <p class="lead">{{ education.description }}</p>
                </template>
            </Card>
        </div>
        <div class="row gap-2 justify-content-center" v-if="experiences?.length" data-aos="fade-up"
        data-aos-duration="2000">
            <Card v-for="experiences in experiences" :key="experiences.id" cards>
                <template #cardHeader>
                    <h4 class="card-title">{{ experiences.company }}</h4>
                </template>
                <template #cardBody>
                    <img :src="experiences.img_url" :alt="experiences.company" loading="lazy" class="img-fluid">
                    <h5 class="lead">{{ experiences.title }}</h5>
                    <p class="lead">{{ experiences.description }}</p>
                </template>
            </Card>
        </div>
        <Spinner v-else />
    </div>
</div>
</template>

<script>
import Card from '@/components/Card.vue';
import Spinner from './Spinner.vue'
export default {
    components: {
        Card,
        Spinner
    },
    computed: {
        education() {
            return this.$store.state.education
        },
        experiences() {
            return this.$store.state.experiences
        }
    },
    mounted() {
        this.$store.dispatch('fetchEducation')
        this.$store.dispatch('fetchExperiences')
    }
}
</script>

<style scoped>
[resume] {
    display: flex;
}

[cards] {
    width: 40%;
}
.img-fluid {
    aspect-ratio: 1;
    object-fit: contain;
    object-position: center;
    height: 9rem;
}
</style>