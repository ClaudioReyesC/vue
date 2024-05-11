<template>
  <div class="result">
    <h2>Resultados</h2>
    <div v-if="dividendoMensual !== null">
      <p>Dividendo Mensual: {{ dividendoMensual }} (UF)</p>
      <p>Sueldo Requerido: {{ sueldoRequerido }} (UF)</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    dividendoMensual: {
      type: Number,
      default: null
    },
    sueldoRequerido: {
      type: Number,
      default: null
    }
  }
};
</script>
<style>
.result {
  background-color: rgb(27, 27, 27);
  color: white;
}

h2 {
  text-align: center;
}

p {
  text-align: center;
}
</style>