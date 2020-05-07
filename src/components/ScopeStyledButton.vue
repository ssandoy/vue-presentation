<template>
  <button v-on:click="func" class="scope-styled-button" :disabled="disabled">
    {{ buttonText }}
  </button>
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
  border-radius: 50%;
  border: none;
  background-color: #d2d2d2;
  width: 30px;
  height: 30px;
  color: white;
}
</style>
