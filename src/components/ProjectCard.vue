<script>
export default {
  name: "ProjectCard",
  props: {
    project: Object,
  },
  data() {
    return {
      baseUrl: "http://127.0.0.1:8000",
    };
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
