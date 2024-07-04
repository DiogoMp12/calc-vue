<template>
  <div id="app" class="container">
    <div class="row">
      <div class="col-md-6 offset-md-3">
        <h1 class="text-center my-4">Calculadora Aritmética</h1>
        <form>
          <div class="mb-3">
            <label for="numero1" class="form-label">Primeiro Número</label>
            <input type="number" class="form-control" id="numero1" v-model.number="numero1">
          </div>
          <div class="mb-3">
            <label for="numero2" class="form-label">Segundo Número</label>
            <input type="number" class="form-control" id="numero2" v-model.number="numero2">
          </div>
          <div class="mb-3">
            <label for="operacao" class="form-label">Operação</label>
            <select id="operacao" class="form-select" v-model="operacao">
              <option value="soma">Soma (+)</option>
              <option value="subtracao">Subtração (-)</option>
              <option value="multiplicacao">Multiplicação (*)</option>
              <option value="divisao">Divisão (/)</option>
            </select>
          </div>
        </form>
        <h3 class="text-center mt-4">Resultado: {{ resultado }}</h3>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      numero1: 0,
      numero2: 0,
      operacao: 'soma'
    };
  },
  computed: {
    resultado() {
      switch (this.operacao) {
        case 'soma':
          return this.numero1 + this.numero2;
        case 'subtracao':
          return this.numero1 - this.numero2;
        case 'multiplicacao':
          return this.numero1 * this.numero2;
        case 'divisao':
          return this.numero2 !== 0 ? this.numero1 / this.numero2 : 'Erro: Divisão por zero';
        default:
          return 0;
      }
    }
  }
};
</script>
<style scoped>
h1, h3 {
  color: #0059ff;
}
</style>