<template>
  <div class="page">
    <div class="page__progress-bar" :style="{ height: diameter + 'px', width: diameter + 'px' }">
      <svg viewBox="0 0 100 100">
        <linearGradient id="linear">
          <stop offset="50%" stop-color="#8932f5" />
          <stop offset="50%" stop-color="#6304d9" />
        </linearGradient>
        <text text-anchor="middle" :dominant-baseline="alignment" x="50" :y="alignmentY" class="page__progress-bar--value">{{ progressValue }}</text>
        <circle
            cx="50" cy="50" r="50"
            fill="transparent"
            :stroke-width="strokeWidth"
            :stroke="inactiveLineColor"
            :stroke-dashoffset="inactiveProgressCircumference"
            stroke-dasharray="314"
            :style="{transition}"
        >
        </circle>
        <circle
            cx="50" cy="50" r="50"
            fill="transparent"
            :stroke-width="strokeWidth"
            :stroke="activeLineColor"
            :stroke-dashoffset="activeProgressCircumference"
            stroke-dasharray="314"
            :style="{transition}"
        >
        </circle>

      </svg>
    </div>
    <form class="page__form page-form">
      <div class="page-form__input">
        <base-input
          label="Цвет фоновой линии"
          :value="inactiveLineColor"
          @update:modelValue="changeInactiveLineColor"
        />
      </div>
      <div class="page-form__input">
        <input type="radio" value="hanging" v-model="alignment" class="checkbox">
        <label>Bottom</label>
      </div>
      <div class="page-form__input">
        <input type="radio" value="central" v-model="alignment" class="checkbox">
        <label>Center</label>
      </div>
      <div class="page-form__input">
        <base-input
            label="Цвет линии прогресса"
            :value="activeLineColor"
            @update:modelValue="changeActiveLineColor"
        />
      </div>
      <div class="page-form__input">
        <base-input
            label="Скорость анимации"
            :value="transitionDuration"
            @update:modelValue="changeTransitionDuration"
        />
      </div>
      <div class="page-form__input">
        <base-input
            label="Цвет линии прогресса"
            :value="transitionTimingFunction"
            @update:modelValue="changeTransitionTimingFunction"
        />
      </div>
      <div class="page-form__input">
        <input-number
            label="Ширина линии"
            :max-value="6"
            :min-value="1"
            :value="strokeWidth"
            :step="0.5"
            @change-value="changeStrokeWidth"
        />
      </div>
      <div class="page-form__input">
        <input-number
            label="Диаметр"
            union="px"
            :min-value="100"
            :max-value="400"
            :value="diameter"
            :step="10"
            @change-value="changeDiameter"
        />
      </div>
      <div class="page-form__input">
        <input-number
            label="Видимая часть окружности"
            union="%"
            :min-value="30"
            :max-value="100"
            :value="visibleCirclePart"
            :step="5"
            @change-value="changeVisibleCirclePart"
        />
      </div>
      <div class="page-form__input">
        <input-number
            label="Значение прогресса"
            union="%"
            :min-value="0"
            :max-value="maxProgressValue"
            :value="progressValue"
            :step="5"
            @change-value="changeProgressValue"
        />
      </div>
      <div class="page-form__input">
        <input-number
            label="Макс. значение прогресса"
            union="%"
            :min-value="0"
            :max-value="100"
            :value="maxProgressValue"
            :step="5"
            @change-value="changeMaxProgressValue"
        />
      </div>
    </form>
  </div>

</template>

<script>
// stroke="url(#linear)" hanging/central
import InputNumber from "./components/InputNumber";
import BaseInput from "./components/BaseInput";
export default {
  name: 'App',
  components: {BaseInput, InputNumber},
  data() {
    return {
      strokeWidth: 5,
      diameter: 220,
      visibleCirclePart: 60,
      progressValue:  95,
      maxProgressValue: 90,
      inactiveLineColor: "#bebbbb",
      activeLineColor: "#974df5",
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
  },
  computed: {
    circumference() {
      return Math.floor(314 * (this.visibleCirclePart / 100))
    },
    activeProgressCircumference() {
      return 314 - Math.floor(this.progressValue * this.circumference / 100)
    },
    inactiveProgressCircumference() {
      return 314 - this.circumference
    },
    transition() {
      return `stroke-dashoffset ${this.transitionDuration} ${this.transitionTimingFunction} 0s`
    },
    alignmentY() {
      return this.alignment === "central" ? 50 : 80
    }
  }
}

</script>

<style lang="scss">
* {
  padding: 0;
  margin: 0;
  border: 0;
}

*,
*:before,
*:after {
  -webkit-box-sizing: border-box;
  box-sizing: border-box;
}

:focus,
:active {
  outline: none;
}

a:focus,
a:active {
  outline: none;
}

nav,
footer,
header,
aside {
  display: block;
}

html,
body {
  height: 100%;
  width: 100%;
  font-size: 100%;
  line-height: 1;
  font-size: 14px;
  -ms-text-size-adjust: 100%;
  -moz-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
}

input,
button,
textarea {
  font-family: inherit;
}

input::-ms-clear {
  display: none;
}

button {
  cursor: pointer;
}

button::-moz-focus-inner {
  padding: 0;
  border: 0;
}

a,
a:visited {
  text-decoration: none;
}

a:hover {
  text-decoration: none;
}

ul li {
  list-style: none;
}

img {
  vertical-align: top;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  font-size: inherit;
  font-weight: 400;
}

* {
  min-height: 0;
  min-width: 0;
}


body {
  padding-top: 30px;
  padding-left: 30px;
  background-color: #161616;
  font-family: Arial;
  color: #fff;
}
.page {
  &__progress-bar {
    display: flex;
    margin-bottom: 160px;
    &--value {
      font-size: 20px;
      fill: #fff;
    }
  }
  svg {
    overflow: visible;
    width: 100%;
  }
}
.input {
  display: block;
  width: 100%;
  height: 100%;
  padding: 1px 5px;
  font-size: 16px;
  background-color: #dad7d7;
}


</style>
