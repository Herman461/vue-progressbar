<template>
  <div class="base-input">
    <div class="base-input__label" v-if="label">{{ label }}</div>
    <div class="base-input__item">
      <input :value="value" class="input" type="text" @input="$emit('update:modelValue', $event.target.value)">
    </div>
  </div>
</template>

<script>
export default {
  name: "base-input",
  props: {
    value: { type: String, required: true },
    label: { type: String }
  },
  model: { prop: "value", event: "input" }
}
</script>

<style lang="scss">
.base-input {
  &__label {
    margin-bottom: 5px;
  }
  &__item {
    height: 30px;
    max-width: 120px;
  }
}
</style>

