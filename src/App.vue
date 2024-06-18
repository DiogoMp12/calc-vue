<template>
  <div id="app" class="container">
    <div class="row">
      <div class="col-md-6 offset-md-3">
        <h1 class="text-center my-4">Calculadora Aritmética</h1>
        <form @submit.prevent="calcularResultado">
          <div class="mb-3">
            <label for="numero1" class="form-label">Primeiro Número</label>
            <input type="number" required class="form-control" id="numero1" v-model.number="numero1">
          </div>
          <div class="mb-3">
            <label for="numero2" class="form-label">Segundo Número</label>
            <input type="number" required class="form-control" id="numero2" v-model.number="numero2">
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
          <button type="submit" class="btn btn-primary w-100" style="border-radius: 50px;">Calcular</button>
        </form>
        <h3 class="text-center mt-4" v-if="resultadoVisivel">Resultado: {{ resultado }}</h3>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      numero1: null,
      numero2: null,
      operacao: 'soma',
      resultado: null,
      resultadoVisivel: false
    };
  },
  methods: {
    calcularResultado() {
      if (this.numero1 === null || this.numero2 === null) {
        alert('Por favor, preencha todos os campos.');
        return;
      }
      
      let res;
      switch (this.operacao) {
        case 'soma':
          res = this.numero1 + this.numero2;
          break;
        case 'subtracao':
          res = this.numero1 - this.numero2;
          break;
        case 'multiplicacao':
          res = this.numero1 * this.numero2;
          break;
        case 'divisao':
          res = this.numero2 !== 0 ? this.numero1 / this.numero2 : 'Erro: Divisão por zero';
          break;
        default:
          res = 0;
      }
      this.resultado = res;
      this.resultadoVisivel = true;
    }
  }
};
</script>

<style scoped>
h1, h3 {
  color: #0059ff;
}
</style>
