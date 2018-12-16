<template>
  <div class="myProjects">
    <ProjectPage/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import ProjectPage from "@/components/ProjectPage.vue";

@Component({
  components: {
    ProjectPage
  }
})
export default class Projects extends Vue {}
</script>
