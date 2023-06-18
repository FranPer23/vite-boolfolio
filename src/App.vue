<script>
import axios from "axios";

export default {
  data() {
    return {
      projects: [],
    };
  },
  mounted() {
    this.getProjects();
  },
  methods: {
    getProjects() {
      axios.get("http://127.0.0.1:8000/api/projects").then((resp) => {
        this.projects = resp.data.results;
      });
    },
  },
};
</script>

<template>
  <div class="container">
    <h2>Progetti</h2>

    <div class="row row-cols-3 g-3">
      <div class="col" v-for="project in projects" :key="project.id">
        <div class="card h-100" style="width: 18rem">
          <img class="card-img-top" src="..." alt="Card image cap" />
          <div class="card-body">
            <h2 class="card-title">{{ project.title }}</h2>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
// @use ".styles/general/scss" as *;
</style>
