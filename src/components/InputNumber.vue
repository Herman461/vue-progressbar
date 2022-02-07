<template>
  <div class="input-number">
    <div class="input-number__button input-number__button--plus">+</div>
    <div class="input-number__item">
      <input class="input" type="text" autocomplete="off" />
    </div>
    <div class="input-number__button input-number__button--minus">-</div>
  </div>
</template>

<script>
export default {
  name: "input-number",

}
</script>

<style lang="scss">
.input-number {
  width: 120px;
  height: 40px;
  display: flex;
  &__button {
    flex: 0 0 40px;
    background-color: #6304d9;
    color: #fff;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 22px;
    font-weight: 700;
  }
  &__item {
    flex: 1 1 auto;

  }
  .input {
    display: block;
    width: 100%;
    height: 100%;
    text-align: center;
    padding: 1px 5px;
  }
}
</style>
