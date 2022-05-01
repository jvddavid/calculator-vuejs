<template>
  <div class="display">
    <span>{{ label }}</span>
  </div>
</template>

<script>
export default {
  name: 'DisplayResult',
  components: {
  },
  props: {
    label: {
      type: String,
      default: '0',
    },
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