<template>
  <div class="box" :class="{'isOn':isOn}">
    <var>{{base}}<sup>{{exponent}}</sup> = {{Math.pow(base,exponent)}}</var>
    <br>
    Hex: {{hexit}}
    <br>
    Binary: {{binary}}
  </div>
</template>

<script>

export default {
  name: 'ToggleablePosition',
  props: ["isOn", "base", "exponent"],
  computed: {
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