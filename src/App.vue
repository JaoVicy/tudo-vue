<script setup>
  import { computed, ref } from 'vue';
  import vueImage from '@/img/vue-img.png';

const number1 = ref(0);
const number2 = ref(0);
const operation = ref("add");

const result = computed(() => {
  switch (operation.value) {
    case "add":
      return number1.value + number2.value;
    case "subtract":
      return number1.value - number2.value;
    case "multiply":
      return number1.value * number2.value;
    case "divide":
      return number2.value !== 0 ? number1.value / number2.value : "Erro: Divisão por zero";
    default:
      return 0;
  }
});

const resetValues = () => {
  number1.value = 0;
  number2.value = 0;
  operation.value = "add";
};
</script>

<template>
  <div class="container">
    <header class="p-5 mb-4 bg-light rounded-3">
      <div class="row align-items-center">
        <!-- Coluna para a imagem -->
        <div class="col-2 text-center">
          <img :src="vueImage" alt="Vue Image" class="img-fluid" style="max-width: 100%;" />
        </div>

        <!-- Coluna para o título e texto -->
        <div class="col-10">
          <h1 class="mb-0">Vue Calculator</h1>
          <p class="mt-3">
            Escolha que operação deseja fazer:
          </p>
        </div>
      </div>
    </header>

    <div class="row justify-content-center">
      <div class="col-md-4">
        <div class="form-group">
          <label for="number1">First Number:</label>

          <input 
          id = "number1"
          v-model.number = "number1"
          type = "number"
          class = "form-control"
          placeholder = "Insert the first number"
          />

        </div>
      </div>

      <div class="col-md-2">
        <div class="form-group">
          <label for="operation">Operation</label>
          <select v-model = "operation" id="operation" class="form-control">
            <option value="add">+</option>
            <option value="subtract">-</option>
            <option value="multiply">*</option>
            <option value="divide">/</option>
          </select>
        </div>
      </div>

      <div class="col-md-4">
        <div class="form-group">
          <label for="number2">Second Number</label>

          <input 
          id = "number2"
          v-model.number = "number2"
          type="number"
          class="form-control"
          placeholder="Insert the second number"
          />
        </div>
      </div>
    </div>
    <div class="row justify-content-center">
      <div class="col-md-6 text-center mt-4">
        <h2>Result: <span class="badge bg-primary">{{ result }}</span></h2>
      </div>
    </div>
    <div class="row justify-content-center mt-4">
      <div class="col-md-6 text-center">
        <button @click="resetValues" class="btn btn-secondary">Default</button>
      </div>
    </div>
    <div class="container">
      <div class="row justify-content-center mt-4">
        <div class="col-md-3">
          <footer class="justify-content-center bg-light">
            <p class="text-center">
              By João, <a href="https://github.com/JaoVicy" class="link-primary">GitHub - JaoVicy</a>
            </p>
          </footer>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
</style>
