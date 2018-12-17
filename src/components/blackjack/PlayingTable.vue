<template>
  <div id="felt">
    <PlayingCards/>
    <TableControls/>
  </div>
</template>

<script lang="ts">
import {Vue, Component} from 'vue-property-decorator';
import PlayingCards from '@/components/blackjack/PlayingCards.vue'; // @ is an alias to /src
import TableControls from '@/components/blackjack/TableControls.vue'; // @ is an alias to /src

@Component({
  components: {
    PlayingCards,
    TableControls,
  },
})
export default class PlayingTable extends Vue {

}

</script>

<style>

#felt {
  background: green;
  height: 100vh;
}
</style>
