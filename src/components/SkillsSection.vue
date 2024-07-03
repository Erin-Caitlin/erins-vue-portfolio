<template>
    <div class="container" skill>
        <div class="row">
            <h2 class="display-2">Skills</h2>
        </div>
        <div class="row gap-2 justify-content-center" v-if="skills?.length">
            <Card v-for="skill in skills" :key="skill.id">
                <template #cardHeader>
                    <h4 class="card-title">{{ skill.language }}</h4>
                </template>
                <template #cardBody>
                    <box-icon type='logo' :name='skill.name' :color="skill.color" id="icon"></box-icon>
                    <p class="lead">{{ skill.level }}</p>
                </template>
            </Card>
        </div>
        <Spinner v-else />
    </div>
</template>
<script>
import Card from './Card.vue'
export default {
    components: {
        Card
    },
    computed: {
        skills() {
            return this.$store.state.skills
        }
    },
    mounted() {
        this.$store.dispatch('fetchSkills')
    }
}
</script>
<style scoped>
[skill] {
    margin: 2rem;
    background: rgb(177, 148, 148)
    url(https://erin-caitlin.github.io/portfolio-images/VuePortfolio/image31.jpg) no-repeat top;
    background-size: cover;
    height: 100vh;
    background-blend-mode: soft-light;
    border-radius: .5rem;
}

#icon {
    font-size: large;
}
</style>