<script>
import axios from "axios";
export default {
  name: "HomePage",
  data() {
    return {
      projects: [],
      // baseUrl: "",
    };
  },
  mounted() {
    this.getProjects();
  },
  methods: {
    getProjects() {
      console.log("getProjects");
      axios.get("http://127.0.0.1:8000/api/projects").then((resp) => {
        console.log(resp);
      });
    },
  },
};
</script>

<template>
  <div></div>
</template>

<style lang="scss" scoped></style>
