<template>
  <div class="page">
    <div class="page__container">
      <base-circle
          :strokeWidth="strokeWidth"
          :diameter="diameter"
          :visibleCirclePart="visibleCirclePart"
          :progressValue="progressValue"
          :maxProgressValue="maxProgressValue"
          :inactiveLineColor="inactiveLineColor"
          :activeLineColor="activeLineColor"
          :transitionDuration="transitionDuration"
          :transitionTimingFunction="transitionTimingFunction"
          :alignment="alignment"
      />
      <form class="page__form">
        <div class="page__form--column">
          <div class="page__form--item">
            <input-number
                label="Ширина линии"
                :max-value="6"
                :min-value="1"
                :value="strokeWidth"
                :step="0.5"
                @change-value="changeStrokeWidth"
            />
          </div>
          <div class="page__form--item">
            <input-number
                label="Диаметр"
                unit="px"
                :min-value="100"
                :max-value="400"
                :value="diameter"
                :step="10"
                @change-value="changeDiameter"
            />
          </div>
          <div class="page__form--item">
            <input-number
                label="Видимая часть окружности"
                unit="%"
                :min-value="30"
                :max-value="100"
                :value="visibleCirclePart"
                :step="5"
                @change-value="changeVisibleCirclePart"
            />
          </div>
          <div class="page__form--item">
            <input-number
                label="Значение прогресса"
                unit="%"
                :min-value="0"
                :max-value="maxProgressValue"
                :value="progressValue"
                :step="5"
                @change-value="changeProgressValue"
            />
          </div>
          <div class="page__form--item">
            <input-number
                label="Макс. значение прогресса"
                unit="%"
                :min-value="0"
                :max-value="100"
                :value="maxProgressValue"
                :step="5"
                @change-value="changeMaxProgressValue"
            />
          </div>
        </div>
        <div class="page__form--column">
          <div class="page__form--item">
            <div class="page__form--item-option">
              <radio-button
                  @update:modelValue="changeAlignment"
                  :model-value="alignment"
                  value="hanging"
                  label="Bottom"
              />
            </div>
            <div class="page-form--item-option">
              <radio-button
                  @update:modelValue="changeAlignment"
                  :model-value="alignment"
                  value="central"
                  label="Center"
              />
            </div>
          </div>
          <div class="page__form--item">
            <base-input
                label="Цвет фоновой линии"
                :value="inactiveLineColor"
                @update:modelValue="changeInactiveLineColor"
            />
          </div>
          <div class="page__form--item">
            <base-input
                label="Цвет линии прогресса"
                :value="activeLineColor"
                @update:modelValue="changeActiveLineColor"
            />
          </div>
          <div class="page__form--item">
            <base-input
                label="Скорость анимации"
                :value="transitionDuration"
                @update:modelValue="changeTransitionDuration"
            />
          </div>
          <div class="page__form--item">
            <base-input
                label="Цвет линии прогресса"
                :value="transitionTimingFunction"
                @update:modelValue="changeTransitionTimingFunction"
            />
          </div>
        </div>
      </form>
    </div>
  </div>

</template>

<script>
import InputNumber from "./InputNumber";
import BaseInput from "./BaseInput";
import BaseCircle from "./BaseCircle";
import RadioButton from "./RadioButton";
export default {
  name: 'base-page',
  components: {RadioButton, BaseCircle, BaseInput, InputNumber},
  data() {
    return {
      strokeWidth: 5,
      diameter: 250,
      visibleCirclePart: 50,
      progressValue:  95,
      maxProgressValue: 100,
      inactiveLineColor: "#bebbbb",
      activeLineColor: "#7422dc",
      transitionDuration: "400ms",
      transitionTimingFunction: "linear",
      alignment: "central"
    }
  },
  methods: {
    changeStrokeWidth(value) {
      this.strokeWidth = value
    },
    changeDiameter(value) {
      this.diameter = value
    },
    changeVisibleCirclePart(value) {
      this.visibleCirclePart = value
    },
    changeProgressValue(value) {
      this.progressValue = value
    },
    changeMaxProgressValue(value) {
      this.maxProgressValue = value
      if (this.progressValue > this.maxProgressValue) {
        this.progressValue = this.maxProgressValue
      }
    },
    changeInactiveLineColor(value) {
      this.inactiveLineColor = value
    },
    changeActiveLineColor(value) {
      this.activeLineColor = value
    },
    changeTransitionDuration(value) {
      this.transitionDuration = value
    },
    changeTransitionTimingFunction(value) {
      this.transitionTimingFunction = value
    },
    changeAlignment(value) {
      this.alignment = value
    },
  },
}

</script>

<style lang="scss">

.page {
  padding-top: 15px;
  &__container {
    max-width: 830px;
    padding: 0 15px;
    margin: 0 auto;
  }
  &__form {
    &--item {
      &:not(:last-child) {
        margin-bottom: 20px;
      }
    }
    &--item-option {
      &:not(last-child) {
        margin-bottom: 6px;
      }
    }
    @media (min-width: 520px) {
      display: flex;
      justify-content: center;
      margin: 0 -30px;
      &--column {
        padding: 0 30px;
      }
    }

    @media (max-width: 520px) {
      &--column {
        &:not(:last-child) {
          margin-bottom: 20px;
        }
      }
    }

  }
}


</style>
