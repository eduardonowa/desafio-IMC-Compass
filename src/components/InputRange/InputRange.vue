<template>
  <div class="input-container">
    <div class="input-labels">
      <label>{{ labelInput }}</label>
      <output>{{ valueSelected }} {{ measure }}</output>
    </div>
    <input
      type="range"
      class="input-range"
      :id="inputId"
      :min="minRange"
      :max="maxRange"
      :step="step"
      @input="event"
    />
  </div>
</template>

<script>
export default {
  name: "InputRange",
  props: {
    labelInput: String,
    valueSelected: String,
    inputId: String,
    minRange: String,
    maxRange: String,
    step: String,
    event: Function,
    measure:String
  },
};
</script>

<style lang="scss" scooped>
@import "./InputRange.scss";
</style>
