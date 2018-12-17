<template>
  <div class="columns">
    <div class="column is-third is-offset-one-third box">
      <nav class="level">
        <button class="button" @click="stick">
          Stand
        </button>
        <button class="button" @click="dealCards(currentPlayer)">
          Hit
        </button>
        <button class="button" @click="dealCards(currentPlayer)">
          Double
        </button>
      </nav>
      <nav class="level">
          Hit
         <img id="optrakLogo" src="@/assets/chip5.svg" style="float: left;"/>
      </nav>
    </div>
  </div>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator';

@Component
export default class TableControls extends Vue {

}

</script>

<style scoped>
#tableControls {
  /* width: 80vw; */
}

</style>
