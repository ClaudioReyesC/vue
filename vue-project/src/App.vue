<template>
  <div>
    <Form @calcular="calcularDividendoYSueldo" />
    <Result :dividendoMensual="dividendoMensual" :sueldoRequerido="sueldoRequerido" />
    <h2 id="Resulcredito">Resultados de Créditos Hipotecarios</h2>
    <div v-if="credits.length === 0">Cargando...</div>
    <div v-else>
      <Card v-for="(credit, index) in credits" :key="index" :creditInfo="credit" />
    </div>
  </div>
</template>

<script>
import Form from "./components/Form.vue";
import Result from "./components/Result.vue";
import Card from "./components/Card.vue";

export default {
  components: {
    Form,
    Result,
    Card
  },
  data() {
    return {
      dividendoMensual: null,
      sueldoRequerido: null,
      credits: [],
      mostrarCreditos: false // Agregamos una variable para controlar la visualización de los créditos hipotecarios
    };
  },
  methods: {
    async fetchCredits() {
      try {
        const response = await fetch("https://api.hipotecarios.info/creditos/?valorPropiedad=2000&Pie=30&Tiempo=20&Dfl2=true");
        const data = await response.json();
        this.credits = data["banco-scotiabank"];
      } catch (error) {
        console.error("Error fetching credits:", error);
      }
    },
    calcularDividendoYSueldo(datos) {
      const montoPrestamo = datos.valorPropiedad - datos.pie;
      const tasaInteresDecimal = datos.tasaInteres / 100;
      const plazoMeses = datos.plazo * 12;
      const cuotaMensual =
        (montoPrestamo * tasaInteresDecimal) /
        (1 - Math.pow(1 + tasaInteresDecimal, -plazoMeses));
      this.dividendoMensual = cuotaMensual.toFixed(2);

      // Calculando sueldo requerido multiplicando por 4 el dividendo mensual
      this.sueldoRequerido = (cuotaMensual * 4).toFixed(2);

      // Luego de calcular los resultados del formulario, mostramos los créditos hipotecarios
      this.mostrarCreditos = true;

      // Llamamos a la función para obtener los créditos hipotecarios
      this.fetchCredits();
    }
  }
};
</script>

<style>
template {
  margin: 0;
}

#Resulcredito {
  color: white;
}
</style>
