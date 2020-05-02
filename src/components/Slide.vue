<template>
  <div class="slide">
    <h1 class="slide__title">{{ slideData.title }}</h1>
    <ul class="slide__list">
      <li class="slide__list__item" v-for="note in slideData.notes" v-bind:key="note" >
        {{ note }}
      </li>
    </ul>
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

<style scoped></style>
