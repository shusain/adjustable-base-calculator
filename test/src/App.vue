<template>
  <input type="number" v-model="base"/>
  <div class="toggle-button-box">
    <ToggleablePosition
      :base="base"
      :exponent="position.exponent"
      :is-on="position.isOn"
      v-for="position of positions"
      :key="position.exponent"
      @click="position.isOn=!position.isOn">
    </ToggleablePosition>
  </div>
  <br/>
  Total (Decimal): {{total}}<br/>
  <div class="row">
    Binary: <var>{{binary}}<sub>2</sub></var>
  </div>
  <div class="row">
    Hex: <var>{{hexit}}<sub>16</sub></var>
  </div>
  <div class="row">
    Octal: <var>{{octal}}<sub>8</sub></var>
  </div>
</template>

<script>

import ToggleablePosition from  './components/ToggleablePosition';

export default {
  name: 'App',
  data() {
    return {
      base: 2,
      positions: []
    }
  },
  computed: {
    total() {
      let retTotal = 0;
      this.positions.forEach(position=>{
        if(position.isOn)
        retTotal += Math.pow(this.base, position.exponent);
      })
      return retTotal
    },
    octal() {
        return this.total.toString(8)
    },
    hexit() {
        return this.total.toString(16)
    },
    binary() {
        return this.total.toString(2)
    }
  },
  created() {
    for (let index = 7; index >= 0; index--) {
      this.positions.push({isOn:false, exponent: index})
      
    }
  },
  components: {
    ToggleablePosition
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
.toggle-button-box {
  display: flex;
  flex-direction: row;
}
input {
  margin-bottom: 1rem;
}
.row {
  display: flex;
  flex-grow: 0;
  flex-direction: row;
}
var {
  font-style: bold;
}
</style>
