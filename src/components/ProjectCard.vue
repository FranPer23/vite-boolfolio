<script>
import store from "../store";

export default {
  name: "ProjectCard",
  props: {
    project: Object,
  },
  data() {
    return {
      store,
    };
  },

  computed: {
    contentPreview() {
      if (!this.project.title) {
        return "Senza titolo";
      } else if (this.project.title.length > 5) {
        return this.project.title.substring(0, 5) + "...";
      } else {
        return this.project.title;
      }
    },
  },
};
</script>

<template>
  <div class="card h-100" style="width: 18rem">
    <img class="card-img-top" src="" alt="inserire img da db" />
    <div class="card-body">
      <h2 class="card-title">{{ project.title }}</h2>
    </div>
  </div>
</template>

<style lang="scss" scoped></style>
