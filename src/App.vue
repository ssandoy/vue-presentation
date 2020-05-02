<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <Slide v-bind:slide-data="slides" />
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Slide from "@/components/Slide.vue";
import slides from "./data/slides.json";

@Component({
  components: {
    Slide
  },
  data() {
    return {
      slides: slides[0]
    };
  }
})
export default class App extends Vue {}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
