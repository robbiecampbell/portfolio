<template>
  <div>
    <PlayingTable/>
  </div>
</template>

<script lang="ts">
import PlayingTable from '@/components/blackjack/PlayingTable.vue';
import { Component, Prop, Vue } from "vue-property-decorator";

@Component({
  components: {
    PlayingTable,
  },
})
export default class ProjectPage extends Vue {}
</script>
