<template>
  <div class="box" :class="{'isOn':isOn}">
    <var>{{base}}<sup>{{exponent}}</sup> = {{Math.pow(base,exponent)}}</var>
    <br>
    <div class="row">
      Binary: <var>{{binary}}<sub>2</sub></var>
    </div>
    <div class="row">
      Hex: <var>{{hexit}}<sub>16</sub></var>
    </div>
    <div class="row">
      Octal: <var>{{octal}}<sub>8</sub></var>
    </div>
  </div>
</template>

<script>

export default {
  name: 'ToggleablePosition',
  props: ["isOn", "base", "exponent"],
  computed: {
    octal() {
        return Math.pow(this.base,this.exponent).toString(8)
    },
    hexit() {
        return Math.pow(this.base,this.exponent).toString(16)
    },
    binary() {
        return Math.pow(this.base,this.exponent).toString(2)
    }
  }
}
</script>

<style>
.box {
    width: 200px;
    height: 200px;
    background: #ff00008f;
    font-size: 24px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin-right:1rem;
    cursor: pointer;
}
.isOn {
    background: rgba(0, 0, 255, 0.479);
}
</style>