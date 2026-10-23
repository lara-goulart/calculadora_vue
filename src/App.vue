<script setup>
  import {reactive} from 'vue'

  const estados = reactive({
    num1: 0,
    num2: 0,
    val: '',
    result: 0,
  })

  function calculate() {

    switch(estados.val) {
      case 'add':
        const added = Number(estados.num1) + Number(estados.num2)
        estados.result =+ added
        return estados.result
      case 'subtract':
        const subtracted = estados.num1 - estados.num2
        estados.result =+ subtracted
        return estados.result
      case 'multiply':
        const multiplied = estados.num1 * estados.num2
        return estados.result =+ multiplied
      case 'divide':
        const divided = estados.num1 / estados.num2
        return estados.result =+ divided
    }
  }
</script>

<template> 
  <div class="body">
    <header>
      <h1>Calculadora</h1>
    </header>
      <div class="container">
        <form id="cu">
          <label for="num1">Digite o primeiro número</label>
          <input @keyup="event1 => estados.num1 = event1.target.value" id="num1" type="number">
          <label for="num2">Digite o segundo número</label>
          <input @keyup ="event2 => estados.num2 = event2.target.value" id="num2" type="number">
          <label for="operation">O que você deseja fazer?</label>
          <select @change="stateVal => estados.val = stateVal.target.value" :calculate() id="operation">
            <option value="">--Por favor selecione uma opção--</option>
            <option value="add">Somar</option>
            <option value="subtract">Subtrair</option>
            <option value="multiply">Multiplicar</option>
            <option value="divide">Dividir</option>
          </select>
        </form>
      </div>
      <p>{{ estados.result }}</p>
    </div>
</template>

<style scoped>
  .body {
    min-height: 100vh;
  }

  header {
    margin-top: 35px;
  }

  h1 {
    text-align: center;
  }

  .container {
    max-width: 1024px;
    margin: 0 auto;
    padding: 20px;
    border-radius: 15px;
    background-color: #004a77;
  }

  form {
    width: 30%;
    display: flex;
    flex-direction: column;
    margin: 0 auto;
  }

  input, select {
    margin: 15px 0 15px 0;
    border-radius: 5px;
    padding: 5px;
    font-size: 15px;
  }

  label {
    font-size: 20px;
    color: #fff;
  }

  p {
    text-align: center;
    font-size: 40px;
    font-weight: bold;
  }

</style>
