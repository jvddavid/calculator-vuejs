<template>
  <div class="display">
    <span>0,00000000000000000</span>
  </div>
</template>

<script>
export default {
  name: 'DisplayResult',
  components: {
  }
}
</script>

<style>
.display {
  max-height: 100%;
  max-width: calc(4 * 25%);
  grid-column: span 4;
  background-color: #0009;
  display: flex;
  justify-content: right;
  align-items: center;
  padding: 0.5em;
  font-size: 2em;
}

.display span {
  display: inline;
  max-height: 2em;
  overflow-y: auto;
  overflow-x: auto;
}
</style>