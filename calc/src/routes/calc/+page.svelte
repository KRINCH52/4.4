<script>
  import { createEventDispatcher } from "svelte";
  const dispatch = createEventDispatcher();

  let num1 = "";
  let num2 = "";
  let action = "+";
  let result = "";

  function calculate() {
    switch (action) {
      case "+":
        result = num1 + num2;
        break;
      case "-":
        result = num1 - num2;
        break;
      case "*":
        result = num1 * num2;
        break;
      case "/":
        result = num1 / num2;
        break;
    }
    dispatch("calculation", { result });
  }
</script>

<main>
  <h1>Калькулятор</h1>
  <input type="number" bind:value={num1} placeholder="Введите первое число" />
  <select bind:value={action}>
    <option value="+">+</option>
    <option value="-">-</option>
    <option value="*">*</option>
    <option value="/">/</option>
  </select>
  <input type="number" bind:value={num2} placeholder="Введите второе число" />
  <button on:click={calculate}>Посчитать</button>
  <p>{result}</p>
</main>

<style>
  h1 {
    color: #000;
  }
  main {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
  }
  input {
    background-color: #333;
    border: 0;
    padding: 5px;
    margin: 10px 0;
    width: 19%;
    color: #fff;
  }
  select {
    color: #fff;
    background-color: #333;
    border: 0;
  }
  button {
    padding: 5px 15px;
    border-radius: 20%;
    box-shadow: #000 2px 2px 2px 2px;
    background-color: #e65c5c;
    color: #fff;
  }
</style>
