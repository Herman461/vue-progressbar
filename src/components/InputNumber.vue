<template>
  <div class="input-number">
    <div class="input-number__label">{{ `${label} (${minValue}-${maxValue}${union})`}}</div>
    <div class="input-number__actions">
      <button
          type="button"
          @click="$emit('change-value', +$refs.input.value - step)"
          class="input-number__button input-number__button--minus"
          :class="{'input-number__button--disabled': doDisableMinusButton}"
          :disabled="doDisableMinusButton"
      >-</button>
      <div class="input-number__item">
        <input ref="input" disabled class="input" :value="value" type="text" autocomplete="off" />
      </div>
      <button
          type="button"
          @click="$emit('change-value', +$refs.input.value + step)"
          class="input-number__button input-number__button--plus"
          :class="{'input-number__button--disabled': doDisablePlusButton}"
          :disabled="doDisablePlusButton"
      >+</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "input-number",
  emits: ['change-value'],
  props: {
    value: { type: Number, required: true },
    step: { type: Number, default: 1 },
    maxValue: { type: Number, default: 100 },
    minValue: { type: Number, default: 1 },
    label: { type: String, default: "" },
    union: { type: String, default: ""}
  },
  methods: {
  },
  computed: {
    doDisableMinusButton() {
      return this.value <= this.minValue
    },
    doDisablePlusButton() {
      return this.value >= this.maxValue
    }
  }
}
</script>

<style lang="scss">
.input-number {
  &__label {
    margin-bottom: 5px;
  }
  &__actions {
    width: 120px;
    height: 40px;
    display: flex;
    border: 1px solid transparent;
    &:hover {
      border-color: red;
    }
  }
  &__button {
    flex: 0 0 40px;
    background-color: #974df5;
    color: #fff;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 22px;
    font-weight: 700;
    &--disabled {
      cursor: not-allowed;
      background-color: #575555;
    }
  }
  &__item {
    flex: 1 1 auto;

  }
  .input {
    text-align: center;
  }
}
</style>
