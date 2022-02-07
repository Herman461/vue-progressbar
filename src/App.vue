<template>
  <div class="page">
    <div class="page__progress-bar">
      <svg height="220" width="220">
        <linearGradient id="linear">
          <stop offset="95%" stop-color="#8932f5" />
          <stop offset="5%" stop-color="#6304d9" />
        </linearGradient>
        <circle cx="110" cy="110" r="100" fill="transparent" stroke-width="strokeWidth" stroke="#8321fc"></circle>
        <circle cx="110" cy="110" r="100" fill="transparent" stroke-width="strokeWidth" stroke="url(#linear)" stroke-dashoffset="100" stroke-dasharray="628"></circle>
      </svg>
    </div>
    <form class="page__form page-form">
      <div class="page-form__input">
        <input-number step="1" @increase-value="changeStrokeWidth" />
      </div>
    </form>
  </div>

</template>

<script>

import InputNumber from "./components/InputNumber";
export default {
  name: 'App',
  components: {InputNumber},
  data() {
    return {
      strokeWidth: 6
    }
  }
  methods: {

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

</style>
