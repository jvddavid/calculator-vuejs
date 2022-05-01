<template>
  <button class="button" :class="{ double, triple, operation }" @click="onClick">
    {{ label }}
  </button>
</template>

<script>
export default {
  name: 'ButtonBase',
  components: {
  },
  props:{
    label: {},
    operation: {
      type: Boolean,
    },
    double: {
      type: Boolean,
    },
    triple: {
      type: Boolean,
    },
    onClick: {
      type: Function,
    },
  }
}
</script>

<style>
:root {
  --bg-button: #f0f0f0;
  --bg-button-hover: #a0a0a0;
  --bg-button-click: #ccc;
  --bg-button-operation: #fa8231;
  --bg-button-operation-hover: #d6671c;
  --bg-button-operation-active: #fa8231cc;
  --border-button: solid 1px #888;
}

.button {
  font-size: 1.4em;
  background-color: var(--bg-button);
  border: none;
  border-right: var(--border-button);
  border-bottom: var(--border-button);
  outline: none;
}

.button:hover {
  background-color: var(--bg-button-hover);
}

.button:active {
  background-color: var(--bg-button-click);
}

.button.double {
  grid-column: span 2;
}

.button.triple {
  grid-column: span 3;
}

.button.operation {
  background-color: var(--bg-button-operation);
  color: #fff;
}

.button.operation:hover {
  background-color: var(--bg-button-operation-hover);
}

.button.operation:active {
  background-color: var(--bg-button-operation-active);
}

</style>