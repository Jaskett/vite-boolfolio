<script>
    import axios from 'axios';
    import ProjectCard from './ProjectCard.vue';

    export default {
        name: 'AppMain',
        data() {
            return {
                projects: [],
            }
        },
        methods: {
            getProjects() {
                axios.get('http://127.0.0.1:8000/api/projects').then((response) => {
                    this.projects = response.data.projects;
                })
            }
        },

        created() {
            this.getProjects();
        },
    };
</script>

<template>
    <div class="container py-5">
        <h1>Progetti</h1>
        
        <div class="row g-4 mt-3">
            <div class="col" v-for="project in projects">
                <ProjectCard :project="project" class="h-100"/>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>

</style>