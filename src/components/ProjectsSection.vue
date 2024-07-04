<template>
    <div class="container">
        <div class="row">
            <h2 class="display-2">Resume</h2>
        </div>
        <div class="row" resume>
        <div class="row gap-2 justify-content-center" v-if="projects?.length">
            <Card v-for="project in projects" :key="project.id">
                <template #cardHeader>
                    <h6>{{ project.project }}</h6>
                    <img :src="project.imgUrl" :alt="project.project" loading="lazy" class="img-fluid">
                </template>
                <template #cardBody>
                    <a class="m-2" :href="project.Github" target="_blank" ><button class="btn btn-danger pro-link">Github</button></a>
                    <a class="m-2" :href="project.Vercel" target="_blank" ><button class="btn btn-danger pro-link">Vercel</button></a>
                </template>
            </Card>
        </div>
        <Spinner v-else />
    </div>
</div>
</template>
<script>
import Card from '@/components/Card.vue';
export default {
    components: {
        Card
    },
    computed: {
        projects() {
            return this.$store.state.projects
        }
    },
    mounted() {
        this.$store.dispatch('fetchProjects')
    }
}
</script>

<style scoped>
/* [resume] {
    display: flex;
} */

.img-fluid {
    aspect-ratio: 1;
    object-fit: contain;
    object-position: center;
    /* height: 9rem; */
}

.card {
    background-color: beige;
}
</style>