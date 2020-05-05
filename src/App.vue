<template>
  <div id="app">
    <div class="col-2">
      <h1>
        <img alt="Vue logo" src="./assets/logo.png" class="app__logo" /> Vue,
        from my point of Vue
        <img alt="Vue logo" src="./assets/logo.png" class="app__logo" />
      </h1>
    </div>
    <div class="col-2">
      <Slide :key="activeSlide" v-bind:slide-data="activeSlide" />
      <ScopeStyledButton
        v-bind:func="prevSlide"
        button-text="Forrige"
        :disabled="isPrevDisabled"
      />
      <ScopeStyledButton
        v-bind:func="nextSlide"
        button-text="Neste"
        :disabled="isNextDisabled"
      />
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Slide from "@/components/Slide.vue";
import slides from "./data/slides.json";
import ScopeStyledButton from "@/components/ScopeStyledButton.vue";

@Component({
  components: {
    ScopeStyledButton,
    Slide
  },
  data: function() {
    return {
      slides: slides,
      activeSlide: slides[0]
    };
  },
  methods: {
    prevSlide: function() {
      this.$data.activeSlide = this.$data.slides[
        this.$data.slides.indexOf(this.$data.activeSlide) - 1
      ];
    },
    nextSlide: function() {
      this.$data.activeSlide = this.$data.slides[
        this.$data.slides.indexOf(this.$data.activeSlide) + 1
      ];
    }
  },
  computed: {
    isPrevDisabled: function() {
      return !this.$data.slides.indexOf(this.$data.activeSlide);
    },
    isNextDisabled: function() {
      return (
        this.$data.slides.indexOf(this.$data.activeSlide) ===
        this.$data.slides.length - 1
      );
    }
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

  display: flex;
  align-items: center;
  flex-direction: column;
}
.app__logo {
  height: 60px;
}
</style>

<!-- TODO LOAD SCSS FROM SOMEWHRE IN A COMPONENT. -->

<!-- TODO RENAEM Col-2 -->
