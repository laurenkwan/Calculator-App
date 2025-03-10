<script setup>
import { ref } from 'vue';

const formula = ref('');

/*
 * FUNCTION: evaluate()
 * PARAMETERS: none
 * FUNCTIONALITY: evaluate() was already written by instructors.
 */
function evaluate() {
  try {
    /* WARNING! Never use eval in production code. */
    // eslint-disable-next-line no-eval
    formula.value = eval(formula.value)
  } catch (exception) {
    console.log("warning: invalid formula", exception);
  }
}

/*
 * FUNCTION: append()
 * PARAMETERS: value: Value to be appended to end of string.
 * FUNCTIONALITY: append() first checks to see if this.formula has been set.
 * If not, then it just replaces the value. If it has been set, it adds the
 * user input string (the button pressed) to the end of this.formula.
 */
function append(value) {
  console.log("TODO: append", value);
  // TODO: append value to this.formula
  if (formula.value === null) {
    formula.value = value;
  } else {
    formula.value += value;
  }

}

/*
 * FUNCTION: backspace()
 * PARAMETERS: none
 * FUNCTIONALITY: backspace() uses slice() to cut the last character off from
 * the string. It uses toString() to ensure that this.formula is a string
 * (otherwise this function would not work when deleting the last character
 * from a result).
 */
function backspace() {
  let str = formula.value.toString()
  formula.value = str.slice(0, -1)
}
</script>

<template>
    <b-container>
      <b-row class="mt-5">
        <b-col cols = "9" >
          <BFormInput :id="`calculator-input`" class="w-100 p-4" v-model="formula"/>
        </b-col>
        <b-col cols = "3">
          <BButton variant="primary" class="w-100 p-4" @click="backspace()">&#x2190;</BButton>
        </b-col>
      </b-row>

      <b-row class="mt-5">
        <b-col cols = "3" class="mb-5">
          <BButton variant="primary" class="w-100 p-4" @click="append('7')">7</BButton>
        </b-col>
        <b-col cols = "3" class="mb-5">
          <BButton variant="primary" class="w-100 p-4" @click="append('8')">8</BButton>
        </b-col>
        <b-col cols = "3" class="mb-5">
          <BButton variant="primary" class="w-100 p-4" @click="append('9')">9</BButton>
        </b-col>
        <b-col cols = "3" class="mb-5">
          <BButton variant="secondary" class="w-100 p-4" @click="append('/')">&#xF7</BButton>
        </b-col>
      </b-row>

      <b-row>
        <b-col cols = "3" class="mb-5" >
          <BButton variant="primary" class="w-100 p-4" @click="append('4')">4</BButton>
        </b-col>
        <b-col cols = "3" class="mb-5">
          <BButton variant="primary" class="w-100 p-4" @click="append('5')">5</BButton>
        </b-col>
        <b-col cols = "3" class="mb-5">
          <BButton variant="primary" class="w-100 p-4" @click="append('6')">6</BButton>
        </b-col>
        <b-col cols = "3" class="mb-5">
          <BButton variant="secondary" class="w-100 p-4" @click="append('*')">&#215</BButton>
        </b-col>
      </b-row>

      <b-row>
        <b-col cols = "3" class="mb-5">
          <BButton variant="primary" class="w-100 p-4" @click="append('1')">1</BButton>
        </b-col>
        <b-col cols = "3" class="mb-5">
          <BButton variant="primary" class="w-100 p-4" @click="append('2')">2</BButton>
        </b-col>
        <b-col cols = "3" class="mb-5">
          <BButton variant="primary" class="w-100 p-4" @click="append('3')">3</BButton>
        </b-col>
        <b-col cols = "3" class="mb-5">
          <BButton variant="secondary" class="w-100 p-4" @click="append('-')">-</BButton>
        </b-col>
      </b-row>

      <b-row>
        <b-col cols = "3" class="mb-5">
          <BButton variant="primary" class="w-100 p-4" @click="append('.')">.</BButton>
        </b-col>
        <b-col cols = "3" class="mb-5">
          <BButton variant="primary" class="w-100 p-4" @click="append('0')">0</BButton>
        </b-col>
        <b-col cols = "3" class="mb-5">
          <BButton variant="success" class="w-100 p-4" @click="evaluate()">=</BButton>
        </b-col>
        <b-col cols = "3" class="mb-5">
          <BButton variant="secondary" class="w-100 p-4" @click="append('+')">+</BButton>
        </b-col>
      </b-row>

    </b-container>
</template>

<style scoped>
</style>
