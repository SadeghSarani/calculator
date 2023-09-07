<script >
  import './assets/styles.scss';

  export default {
    name : 'App',
    
    data(){
      return {
        currentNumber : "",
        prevNumber : "",
        total : "",
      }
    },
    methods : {
      addNumber(data) {
        if(this.currentNumber == 0 && data ==0 ) return;
        this.currentNumber+=data;
      },
      addDot() {
          if( this.currentNumber.includes('.') ) return;

          this.currentNumber += ".";
      },
      clear() {
          if(this.currentNumber == "") return;

          this.currentNumber = " ";
      },
      plusMinus() {
        if(parseFloat(this.currentNumber) > 0) {
          this.currentNumber = '-' + this.currentNumber;
        }else {
          this.currentNumber = this.currentNumber.substring(1);
        } 
      },
      handleOperation (operation) {
        this.prevNumber = this.currentNumber;
        this.currentNumber = "";
        this.operation = operation;
      },
      equal() {
         switch (this.operation) {
           case '+' : 
            this.currentNumber = parseFloat(this.prevNumber) + parseFloat(this.currentNumber);
            break;
           case '-' :
              this.currentNumber = parseFloat(this.prevNumber) - parseFloat(this.currentNumber);
              break;
            case '%' : 
              this.currentNumber = parseFloat(this.prevNumber) % parseFloat(this.currentNumber);
              break;
            case '*' :
              this.currentNumber = parseFloat(this.prevNumber) * parseFloat(this.currentNumber);
              break;
            case '/' :
              this.currentNumber = parseFloat(this.prevNumber) / parseFloat(this.currentNumber);
              break;
         }
      }
    }
  }
</script>

<template>
  <main>
    <input type="string" v-model="currentNumber" />
    <div class='keys'>
      <button class='op__key' op='clear' @click="clear">C</button>
      <button class='op__key' op='negate' @click="plusMinus" >+/-</button>
      <button class='op__key' op='percent' @click="handleOperation('%')">%</button>
      <button class='op__key' op='divide' @click="handleOperation('/')">/</button>
      <button class='num__key' @click="addNumber(7)">7</button>
      <button class='num__key' @click="addNumber(8)">8</button>
      <button class='num__key' @click="addNumber(9)">9</button>
      <button class='op__key' op='multiply' @click="handleOperation('*')">x</button>
      <button class='num__key' @click="addNumber(4)">4</button>
      <button class='num__key' @click="addNumber(5)">5</button>
      <button class='num__key' @click="addNumber(6)">6</button>
      <button class='op__key' op='subtract' @click="handleOperation('-')" >-</button>
      <button class='num__key' @click="addNumber(1)">1</button>
      <button class='num__key' @click="addNumber(2)">2</button>
      <button class='num__key' @click="addNumber(3)">3</button>
      <button class='op__key' op='add' @click="handleOperation('+')">+</button>
      <span></span>
      <button class='num__key' @click="addNumber(0)">0</button>
      <button class='num__key' @click="addDot()">.</button>
      <button class='eq__key' @click="equal">=</button>
    </div>
  </main>
</template>


