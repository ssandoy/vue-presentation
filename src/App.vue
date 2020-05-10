<template>
  <div id="app">
    <div class="col-2">
      <Slide :key="activeSlide" v-bind:slide-data="activeSlide" />
      <div class="app__button-group">
        <ScopeStyledButton
          v-bind:func="prevSlide"
          button-text="<"
          :disabled="isPrevDisabled"
        />
        <div class="app__slide-number">
          {{ slides.indexOf(activeSlide) + 1 }}
        </div>
        <ScopeStyledButton
          v-bind:func="nextSlide"
          button-text=">"
          :disabled="isNextDisabled"
        />
      </div>
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
body {
  background-color: #f2f2f2;
}
#app {
  /*font-family: Avenir, Helvetica, Arial, sans-serif;*/
  font-family: Impact serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 40px;

  display: flex;
  align-items: center;
  flex-direction: column;
}
.app {
  &__logo {
    height: 60px;
  }

  &__slide-number {
    border-radius: 50%;
    background-color: #42b983;
    width: 30px;
    height: 30px;
    display: flex;
    align-items: center;
    justify-content: center;
    color: white;
  }

  &__button-group {
    display: flex;
    flex-direction: row;
    justify-content: center;
    button {
      margin: 0 5px;
    }
  }
}

@font-face {
  font-family: Impact;
  src: url("./assets/impact.ttf");
}
</style>

<!-- TODO LOAD SCSS FROM SOMEWHRE IN A COMPONENT. -->

<!-- TODO RENAEM Col-2 -->
