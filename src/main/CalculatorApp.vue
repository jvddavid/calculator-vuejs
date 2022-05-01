<template>
  <div class="calculator">
    <display-result :label="displayValue"></display-result>
    <button-base :label="'AC'" :triple="true" :operation="true" :onClick="clearMemory"></button-base>
    <button-base :label="'*'" :operation="true" :onClick="setOperation"></button-base>
    <button-base :label="'7'" :onClick="addDigit"></button-base>
    <button-base :label="'8'" :onClick="addDigit"></button-base>
    <button-base :label="'9'" :onClick="addDigit"></button-base>
    <button-base :label="'/'"  :operation="true" :onClick="setOperation"></button-base>
    <button-base :label="'4'" :onClick="addDigit"></button-base>
    <button-base :label="'5'" :onClick="addDigit"></button-base>
    <button-base :label="'6'" :onClick="addDigit"></button-base>
    <button-base :label="'+'"  :operation="true" :onClick="setOperation"></button-base>
    <button-base :label="'1'" :onClick="addDigit"></button-base>
    <button-base :label="'2'" :onClick="addDigit"></button-base>
    <button-base :label="'3'" :onClick="addDigit"></button-base>
    <button-base :label="'-'"  :operation="true" :onClick="setOperation"></button-base>
    <button-base :label="'0'" :onClick="addDigit" :double="true"></button-base>
    <button-base :label="'.'" :onClick="addDigit"></button-base>
    <button-base :label="'='"  :operation="true" :onClick="setOperation"></button-base>
  </div>
</template>

<script>
import DisplayResult from '@/components/DisplayResult.vue'
import ButtonBase from '@/components/ButtonBase.vue'
export default {
  name: 'CalculatorApp',
  components: { DisplayResult, ButtonBase },
  data: function () {
    return {
      displayValue: '0',
      lastDigit: null
    }
  },
  methods: {
    clearMemory() {
      this.displayValue = '0'
      this.lastDigit = null
    },
    setOperation(operation) {
      let newDisplayValue = this.displayValue;
      let match = newDisplayValue.match(/(.*)[*,/,+,-]$/);
      while (match !== null) {
        newDisplayValue = match[1];
        match = newDisplayValue.match(/(.*)[*,/,+,-]$/);
      }
      
      switch (operation) {
        case "=":
          if (this.lastDigit === null || this.lastDigit === "=") {
            break;
          }
          match = newDisplayValue.match(/^([-]?[0-9.]*)[*,/,+,-]([-]?[0-9.]*)/m);
          while (match !== null) {
            match = newDisplayValue.match(
              /^([-]?[0-9.]*)[*,/,+,-]([-]?[0-9.]*)/m
            );
            if (match === null) break;
            if (match[1] === "") break;
            const n1 = Number(match[1]);
            const n2 = Number(match[2]);
            let n3 = 0;
            const op = match[0].replace(match[1], "").replace(match[2], "");
            switch (op) {
              case "+":
                n3 = n1 + n2;
                break;
              case "-":
                n3 = n1 - n2;
                break;
              case "*":
                n3 = n1 * n2;
                break;
              case "/":
                n3 = n1 / n2;
                break;
              default:
                break;
            }
            console.log(newDisplayValue);
            newDisplayValue = newDisplayValue.replace(
              /^([-]?[0-9.]*)[*,/,+,-]([-]?[0-9.]*)/m,
              n3.toString()
            );
          }
          if (
            newDisplayValue.includes("NaN") ||
            newDisplayValue.includes("Infinity")
          ) {
            this.clearMemory();
            break;
          }
          this.displayValue = newDisplayValue;
          this.lastDigit = operation;
          break;
        case "-":
          if (
            this.lastDigit !== "-" &&
            "*/+".includes(this.lastDigit)
          ) {
            this.displayValue = newDisplayValue + (this.lastDigit || "") + operation,
            this.lastDigit = operation;
            break;
          }
          this.displayValue = newDisplayValue + operation,
          this.lastDigit = operation;
          break;
        default:
          this.displayValue = newDisplayValue + operation,
          this.lastDigit = operation;
          break;
      }
    },
    addDigit(n) {
      let newDisplayValue = this.displayValue;
      let lastNumber = this.displayValue;
      const match = lastNumber.match(/[*,/,+,-]([0-9.-]*)/);
      if (match !== null) {
        lastNumber = match[1];
        if (match[0].includes("-")) {
          lastNumber = "-" + lastNumber;
        }
      }
      if (lastNumber === "0" && n === "0") {
        return;
      } else if (lastNumber === "0") {
        lastNumber = "";
      }
      if (newDisplayValue === "0") {
        newDisplayValue = "";
      }
      if (
        newDisplayValue.includes("NaN") ||
        newDisplayValue.includes("Infinity")
      ) {
        return this.clearMemory();
      }
      if (n === "." && lastNumber.includes(".")) {
        return;
      }
      this.lastDigit = n;
      this.displayValue = newDisplayValue + n;
    },
  },
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