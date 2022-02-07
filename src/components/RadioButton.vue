<template>
  <label class="radio-button">
    <input
        type="radio"
        :value="value"
        v-model="modelValue"
        class="checkbox"
        @input="$emit('update:modelValue', $event.target.value)"
    >
    <span>{{label}}</span>
  </label>
</template>

<script>
export default {
  name: "radio-button",
  props: {
    modelValue: {type: String, required: true},
    value: {type: String, required: true},
    label: {type: String, required: true}
  },
  model: {prop: "modelValue", event: "input"}
}
</script>


<style scoped lang="scss">
.radio-button {
  input {
    display: none;
  }
  input:checked + span::after {
    transform: scale(1);
  }
  span {
    display: inline-flex;
    align-items: center;
    position: relative;

    &::before {
      content: "";
      width: 20px;
      height: 20px;
      margin-right: 8px;
      align-self: flex-start;

      border-radius: 50%;
      background-color: #fff;
    }
    &::after {
      content: "";
      position: absolute;
      top: 3px;
      left: 3px;
      width: 14px;
      height: 14px;

      transition: all 0.3s ease 0s;
      transform: scale(0);

      border-radius: 50%;
      background-color: #974df5;
    }
  }
}
</style>
