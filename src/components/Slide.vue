<template>
  <div class="slide">
    <div class="slide__title">
      <h1 v-if="slideData.title" class="slide__title--h1">
        {{ slideData.title }}
      </h1>
      <img
        class="slide__title--icon"
        v-if="slideData.titleIcon"
        v-bind:src="slideData.titleIcon"
        alt="title-icon"
      />
    </div>
    <div class="slide__container">
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
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";
type SlideData = {
  title: string;
  titleIcon?: string;
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
  &__container {
    border: 1px solid black;
    width: 60vw;
    height: 70vh;
    margin: 1rem 0;
    background-color: white;

    display: grid;
    grid-template-columns: 5% 35% 5% 50% 5%;
    grid-template-rows: 10% 80% 10%;
  }

  &__title {
    &--icon {
      height: 50px;
    }
    &--h1 {
      margin: 0;
    }
  }

  &__image {
    justify-self: center;
    align-self: center;
    grid-row: 2;

    &--whole {
      grid-column-start: 2;
      grid-column-end: 5;
      max-height: 100%;
      max-width: 100%;
    }

    &--half {
      grid-column: 4;
      width: 100%;
    }
  }

  &__list {
    grid-column: 2;
    grid-row: 2;
    align-self: center;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    height: 100%;
    p {
      text-align: right;
      font-size: 20px;
      color: black;
      margin: 5px;
      &:before {
        /*content: "-";*/
        margin-right: 10px;
      }
    }
  }
}
</style>
