<template>
  <div id="header">
    <h1 id="heading" class="title is-1">Robbie Campbell</h1>
    <h1 id="subHeading" class="subtitle is-1">Software Developer</h1>

    <span class="icon is-large">
      <i id="downArrow" class="fas fa-angle-double-right" @click="scrollDown"></i>
    </span>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class HomePage extends Vue {

  private scrollDown () {
    console.log("scrollDown")
    this.$router.push('projects')
  }

}
</script>

<style scoped>

#header {
  height: 100vh;
}

#heading, #subHeading, #downArrow {
  color: white;
  text-align: center;
}

</style>
