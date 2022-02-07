<template>
  <div class="progress-bar" :style="{ height: diameter + 'px', width: diameter + 'px' }">
    <svg viewBox="0 0 100 100">
      <text text-anchor="middle" :dominant-baseline="alignment" x="50" :y="alignmentY" class="progress-bar__value">{{ progressValue }}</text>
      <circle
          cx="50" cy="50" r="50"
          fill="transparent"
          :stroke-width="strokeWidth"
          :stroke="inactiveLineColor"
          :stroke-dashoffset="inactiveProgressCircumference"
          stroke-dasharray="314"
          transform="rotate(90 50 50)"
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
          transform="rotate(90 50 50)"
          :style="{transition}"
      >
      </circle>

    </svg>
  </div>
</template>

<script>
export default {
  name: "base-circle",
  props: {
    strokeWidth: {type: Number, default: 5},
    diameter: {type: Number, default: 250},
    visibleCirclePart: {type: Number, default: 50},
    progressValue: {type: Number, default: 95},
    maxProgressValue: {type: Number, default: 100},
    inactiveLineColor: {type: String, default: "#bebbbb"},
    activeLineColor: {type: String, default: "#974df5"},
    transitionDuration: {type: String, default: "400ms"},
    transitionTimingFunction: {type: String, default: "linear"},
    alignment: {type: String, default: "central"}
  },
  computed: {
    alignmentY() {
      return this.alignment === "central" ? 50 : 80
    },
    activeProgressCircumference() {
      return 314 - Math.floor(this.progressValue * this.circumference / 100)
    },
    inactiveProgressCircumference() {
      return 314 - this.circumference
    },
    circumference() {
      return Math.floor(314 * (this.visibleCirclePart / 100))
    },
    transition() {
      return `stroke-dashoffset ${this.transitionDuration} ${this.transitionTimingFunction} 0s`
    },
  }
}
</script>


<style scoped lang="scss">
.progress-bar {
  display: flex;
  text-align: center;
  margin: 0 auto 60px auto;
  svg {
    overflow: visible;
    width: 100%;
  }
  &__value {
    font-size: 20px;
    fill: #fff;
  }
}

</style>
