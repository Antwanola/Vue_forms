<template>
  <div class="container">
  <h1> Home page</h1>
 <p>Score: {{ score}}</p>
 <button class="first" @click="start" :disabled="isPlaying">Change Name</button>
 <BlockContainer v-if="isPlaying" :delay="delay" @reactTimer="endGame"/>
  </div>

</template>

<script lang="ts">
import { defineComponent } from 'vue';
import BlockContainer from '../components/BlockContainer.vue'

export default defineComponent({
  name: 'HomeView',
  components: {BlockContainer},
  data() {
    return {
      isPlaying: false,
      delay: 0,
      score: 0
    }
  },
  methods: {
    start(){
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = !this.isPlaying;
      console.log(this.delay);
    },
    endGame(eventGetter: number) {
      this.score = eventGetter
    }
  }
  })
</script>
 <style>
.container {
  display: flex;
  flex-direction: column;
}
.first {
  padding: 2%
}
</style>