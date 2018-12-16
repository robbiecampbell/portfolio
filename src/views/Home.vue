<template>
  <div class="home">
    <HomePage/>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import HelloWorld from "@/components/HelloWorld.vue"; // @ is an alias to /src
import HomePage from "@/components/HomePage.vue"; // @ is an alias to /src
import ProjectPage from "@/components/ProjectPage.vue"; // @ is an alias to /src

@Component({
  components: {
    HelloWorld,
    HomePage,
    ProjectPage
  }
})
export default class Home extends Vue {}
</script>

<style scoped>
  .home {
    background-color: #171123;
    height: 100vh;
  }
</style>
