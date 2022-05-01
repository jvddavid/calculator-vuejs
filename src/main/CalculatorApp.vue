<template>
  <div class="calculator">
    <display-result></display-result>
    <button-base :label="'AC'" :triple="true" :operation="true"></button-base>
    <button-base :label="'/'" :operation="true"></button-base>
    <button-base :label="'7'"></button-base>
    <button-base :label="'8'"></button-base>
    <button-base :label="'9'"></button-base>
    <button-base :label="'*'"  :operation="true"></button-base>
  </div>
</template>

<script>
import DisplayResult from '@/components/DisplayResult.vue'
import ButtonBase from '@/components/ButtonBase.vue'
export default {
  name: 'CalculatorApp',
  components: { DisplayResult, ButtonBase },
}
</script>

<style>
.calculator {
  height: 320px;
  width: 235px;
  border-radius: 5px;
  overflow: hidden;

  display: grid;
  grid-template-columns: repeat(4, 25%);
  grid-template-rows: 1fr repeat(5, 48px);
}

</style>