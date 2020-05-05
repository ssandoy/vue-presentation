<template>
  <div class="slide">
    <h1 class="slide__title">{{ slideData.title }}</h1>
    <img
      v-if="slideData.image"
      v-bind:class="{
        slide__image: true,
        'slide__image--half': !!slideData.notes.length,
        'slide__image--whole': !slideData.notes.length
      }"
      v-bind:src="slideData.image"
    />
    <div
      v-bind:class="{
        slide__list: !!slideData.notes.length
      }"
    >
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
  height: 70vh;
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
    grid-row: 3;

    &--whole {
      grid-column-start: 2;
      grid-column-end: 5;
      height: 100%;
    }

    &--half {
      grid-column: 4;
      width: 100%;
    }
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
