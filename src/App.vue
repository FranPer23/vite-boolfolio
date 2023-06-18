<script>
import axios from "axios";
import store from "./store";
import ProjectCard from "./components/ProjectCard.vue";

export default {
  data() {
    return {
      projects: [],
      currentPage: 1,
      lastPage: null,
      totalProjects: 0,
      store,
    };
  },
  mounted() {
    this.getProjects();
  },
  methods: {
    getProjects(pageNumber = 1) {
      axios
        .get(`${store.apiBaseUrl}/api/projects`, {
          params: {
            page: pageNumber,
          },
        })
        .then((resp) => {
          this.projects = resp.data.results.data;
          this.currentPage = resp.data.results.current_page;
          this.lastPage = resp.data.results.last_page;
          this.totalProjects = resp.data.results.total;
        });
    },
  },
  components: { ProjectCard },
};
</script>

<template>
  <div class="container">
    <h2>Progetti</h2>
    <div class="">
      <h3>Progetti trovati: {{ totalProjects }}</h3>
    </div>
    <div class="row row-cols-3 g-3 mb-3">
      <div class="col" v-for="project in projects" :key="project.id">
        <ProjectCard :project="project" />
      </div>
    </div>

    <!-- PAGINAZIONE -->
    <nav v-if="lastPage" aria-label="Page navigation example">
      <ul class="pagination">
        <li class="page-item">
          <a
            @click.prevent="getProjects(currentPage - 1)"
            :class="{ disabled: currentPage === 1 }"
            class="page-link"
            href="#"
            aria-label="Previous"
          >
            <span aria-hidden="true">&laquo;</span>
            <span class="sr-only">Previous</span>
          </a>
        </li>
        <li class="page-item" v-for="pageNum in lastPage">
          <a
            @click.prevent="getProjects(pageNum)"
            :class="{ active: currentPage === currentPage }"
            class="page-link"
            href="#"
            >{{ pageNum }}</a
          >
        </li>

        <li class="page-item">
          <a
            @click.prevent="getProjects(currentPage + 1)"
            :class="{ disabled: currentPage === lastPage }"
            class="page-link"
            href="#"
            aria-label="Next"
          >
            <span aria-hidden="true">&raquo;</span>
            <span class="sr-only">Next</span>
          </a>
        </li>
      </ul>
    </nav>
  </div>
</template>

<style lang="scss">
// @use ".styles/general/scss" as *;
</style>
