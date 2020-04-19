<template>
  <div class="calculator">
    <div class="screen">{{ result || '0' }}</div>
    <div @click="clear" class="btn">C</div>
    <div @click="presign" class="btn">+/−</div>
    <div @click="percent" class="btn">%</div>
    <div @click="divide" class="btn operator">÷</div>
    <div @click="type(7)" class="btn">7</div>
    <div @click="type(8)" class="btn">8</div>
    <div @click="type(9)" class="btn">9</div>
    <div @click="multiply" class="btn operator">×</div>
    <div @click="type(4)" class="btn">4</div>
    <div @click="type(5)" class="btn">5</div>
    <div @click="type(6)" class="btn">6</div>
    <div @click="subtract" class="btn operator">-</div>
    <div @click="type(1)" class="btn">1</div>
    <div @click="type(2)" class="btn">2</div>
    <div @click="type(3)" class="btn">3</div>
    <div @click="add" class="btn operator">+</div>
    <div @click="type(0)" class="btn span-2">0</div>
    <div @click="dot" class="btn">.</div>
    <div @click="equal" class="btn operator">=</div>
  </div>
</template>

<script>
export default {
  name: 'Calculator',
  data() {
    return {
      result: '',
      previous: null,
      operator: null,
      operationActive: false,
    }
  },
  methods: {
    clear() {
      this.result = '';
    },
    type(number) {
      if (this.operationActive) {
        this.result = '';
        this.operationActive = false;
      }
      this.result =  this.result === '0' ? `${number}` : `${this.result}${number}`;
    },
    presign() {
      this.result = this.result.charAt(0) === '-' ? `${this.result.slice(1)}` : `-${this.result}`;
    },
    percent() {
      if (this.result !== '0') {
        this.result = `${parseFloat(this.result) / 100}`;
      }
    },
    dot() {
      if (this.result.indexOf('.') === -1) {
        this.result = `${this.result}.`;
      }
    },
    setPrevious() {
      this.previous = this.result;
      this.operationActive = true;
    },
    calculate() {
      if (this.previous !== null) {
        this.equal();
      }
    },
    divide() {
      this.calculate();
      this.operator = (a, b) => (a / b);
      this.setPrevious();
    },
    multiply() {
      this.calculate();
      this.operator = (a, b) => (a * b);
      this.setPrevious();
    },
    subtract() {
      this.calculate();
      this.operator = (a, b) => (a - b);
      this.setPrevious();
    },
    add() {
      this.calculate();
      this.operator = (a, b) => (a + b)
      this.setPrevious();
    },
    equal() {
      this.result = `${this.operator(parseFloat(this.previous), parseFloat(this.result))}`;
      this.previous = null;
    }
  }
}
</script>

<style scoped>
  .calculator {
    max-height: 380px;
    max-width: 350px;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    grid-auto-rows: 60px;
    margin: auto;
    position: fixed;
    left:0; 
    right:0;
    top:0; 
    bottom:0;
    font-weight: bold;
    background-color: #1B051F;
    padding: 10px;
    border-radius: 10px;
  }

  .screen,
  .btn {
    -moz-user-select: none;
   -khtml-user-select: none;
   -webkit-user-select: none;
   -ms-user-select: none;
   user-select: none;
  }

  .screen {
    grid-column: 1/5;
    background-color: #282828;
    border: 1px solid #282828;
    border-radius: 10px;
    margin: 1px;
    padding: 0 10px;
    color: white;
    text-align: right;
    vertical-align: middle;
    line-height: 60px;
  }

  .span-2 {
    grid-column: 1/3;
  }

  .btn {
    background-color: #E8E0E0;
    border: 1px solid #E8E0E0;
    border-radius: 10px;
    margin: 1px;
    text-align: center;
    vertical-align: middle;
    line-height: 60px;
  }

  .operator {
    background-color: #714068;
    border: 1px solid #714068;
    color: white;
  }

  .btn:hover,
  .operator:hover {
    opacity: 0.9;
  }
</style>
