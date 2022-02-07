<template>
  <label class="base-input">
    <span class="base-input__label" v-if="label">{{ label }}</span>
    <input :value="value" class="input" type="text" @input="$emit('update:modelValue', $event.target.value)">
  </label>
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
  span {
    display: inline-block;
    margin-bottom: 3px;
  }
  input {
    height: 30px;
    max-width: 120px;
  }
}
</style>

