<template>
  <div id="app">
    <h1>CalculatorApp</h1>
    <calculator-app></calculator-app>
  </div>
</template>

<script>
import CalculatorApp from './main/CalculatorApp.vue'

export default {
  name: 'App',
  components: {
    CalculatorApp
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto+Mono:wght@100&display=swap');
* {
  font-family: 'Roboto Mono', monospace;
  padding: 0;
  margin: 0;
}

html,
body {
  height: 100%;
}

#app {
  height: 100%;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  color: #fff;
  background: #00bf8f;  /* fallback for old browsers */
  background: -webkit-linear-gradient(to right, #001510, #00bf8f);  /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(to right, #001510, #00bf8f); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
}


::-webkit-scrollbar {
  background: #00f260; /* fallback for old browsers */
  background: -webkit-linear-gradient(
    to left,
    #0575e6,
    #00f260
  ); /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(
    to left,
    #0575e6,
    #00f260
  ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
  width: 0.5rem;
  height: 0.5rem;
  border-radius: 1rem;
}

/* background of the scrollbar except button or resizer */
::-webkit-scrollbar-track {
  background: #00f260; /* fallback for old browsers */
  background: -webkit-linear-gradient(
    to left,
    #0575e6,
    #00f260
  ); /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(
    to left,
    #0575e6,
    #00f260
  ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */
  border-radius: 1rem;
}

/* scrollbar itself */
::-webkit-scrollbar-thumb {
  background-color: #0004;
  border-radius: 1rem;
}

/* set button(top and bottom of the scrollbar) */
::-webkit-scrollbar-button {
  display: none;
}

</style>
