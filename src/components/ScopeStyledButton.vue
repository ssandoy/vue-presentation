<template>
  <button v-on:click="func" class="scope-styled-button" :disabled="disabled">{{ buttonText }}</button>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class ScopeStyledButton extends Vue {
  @Prop({ required: true }) buttonText!: string;
  @Prop({ required: true }) func: any;
  @Prop() disabled!: boolean;
}
</script>

<style scoped lang="scss">
.scope-styled-button {
  background-color: deeppink;
  color: deepskyblue;
}
</style>
