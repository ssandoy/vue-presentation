<template>
  <div class="slide">
    <h1 class="slide__title">{{ slideData.title }}</h1>
    <img
      v-if="slideData.image"
      class="slide__image"
      v-bind:src="slideData.image"
    />
    <div class="slide__list">
      <p
        class="slide__list__item"
        v-for="note in slideData.notes"
        v-bind:key="note + slideData"
      >
        {{ note }}
      </p>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
type SlideData = {
  title: string;
  image?: string;
  notes: string[];
};

@Component
export default class Slide extends Vue {
  @Prop({ required: true }) private slideData!: SlideData;
}
</script>

<style scoped lang="scss">
.slide {
  border: 1px solid black;
  width: 60vw;
  height: 50vh;
  margin: 1rem 0;

  display: grid;
  grid-template-columns: 5% 42% 5% 42% 5%;
  grid-template-rows: 10% 10% 70% 10%;

  &__title {
    grid-row: 1;
    grid-column: span 5;
  }

  &__image {
    justify-self: center;
    align-self: center;
    width: 100%;
    grid-column: 4;
    grid-row: 3;
  }

  &__list {
    grid-column: 2;
    grid-row: 3;
    align-self: center;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    height: 100%;
    p {
      text-align: left;
      font-size: 20px;
      margin: 5px;
      &:before {
        content: "-";
        margin-right: 10px;
      }
    }
  }
}
</style>
