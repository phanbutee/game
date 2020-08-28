<template>
  <div style="background-color: black">
    <div id="app">
      <h1>Cosmic battle</h1>
      <Counter label />
      <br />
      <br />
    </div>
  </div>
</template>
<script>
import Counter from "./components/Counter";
export default {
  name: "App",
  components: {
    Counter,
  },
  data: function () {
    return {
      total1: 0,
      total2: 0,
    };
  },
  methods: {
    sum(counterValue) {
      this.total1 = counterValue;
    },

    sum1(counterValue) {
      this.total2 = counterValue;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: red;
  margin: auto;
}
</style>