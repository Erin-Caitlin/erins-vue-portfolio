<template>
    <div class="container" skill>
        <div class="row">
            <h2 class="display-2">Skills</h2>
        </div>
        <div class="row gap-2 justify-content-center" v-if="skills?.length">
            <div v-for="skill in skills" :key="skill.id">
                    <h4 class="card-title">{{ skill.language }}</h4>
                    <box-icon type='logo' :name='skill.name' :color="skill.color" id="icon"></box-icon>
                    <p class="lead">{{ skill.level }}</p>
            </div>
        </div>
        <Spinner v-else />
    </div>
</template>
<script>
import Spinner from './Spinner.vue'
export default {
    components: {
        Spinner
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
#icon {
    font-size: 50%;
}
</style>