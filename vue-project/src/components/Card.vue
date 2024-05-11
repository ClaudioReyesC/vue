<template>
  <div class="tarjeta-container">
    <div class="tarjeta">
      <h3 v-if="!showAllInfo">{{ creditInfo.banco.nombre }}</h3>
      <p v-if="!showAllInfo">Tasa de Interés: {{ creditInfo.tasaDeInteres }}</p>
      <p v-if="!showAllInfo">Costo Total: {{ creditInfo.costoTotal }}</p>
      <p v-if="!showAllInfo">Gastos Operacionales: {{ creditInfo.gastosOperacionales }}</p>
      <p v-if="!showAllInfo">Máximo Plazo: {{ creditInfo.maximoPlazo }}</p>
      <p v-if="!showAllInfo">Periodo de Gracia: {{ creditInfo.periodoDeGracia.valor }}</p>
      <button v-if="!showAllInfo" @click="showAllInfo = true" class="button" id="vermas">Ver más</button>
      <div v-if="showAllInfo">
        <h3>{{ creditInfo.banco.nombre }}</h3>
        <p>Tasa de Interés: {{ creditInfo.tasaDeInteres }}</p>
        <p>Costo Total: {{ creditInfo.costoTotal }}</p>
        <p>Gastos Operacionales: {{ creditInfo.gastosOperacionales }}</p>
        <p>Máximo Plazo: {{ creditInfo.maximoPlazo }}</p>
        <p>Periodo de Gracia: {{ creditInfo.periodoDeGracia.valor }}</p>
        <p>Financiamiento Hasta: {{ creditInfo.financiamientoHasta.valor }}</p>
        <p>Características: {{ creditInfo.caracteristicas }}</p>
        <ul>
          <li v-for="(req, index) in creditInfo.requisitos" :key="index">{{ req }}</li>
        </ul>
        <h4>Gastos Operacionales:</h4>
        <ul>
          <li v-for="(op, index) in creditInfo.gastosOperacionalesText" :key="index">{{ op }}</li>
        </ul>
        <h4>Seguros Incluidos:</h4>
        <ul>
          <li v-for="(seg, index) in creditInfo.segurosIncluidos" :key="index">{{ seg }}</li>
        </ul>
        <h4>Observaciones:</h4>
        <ul>
          <li v-for="(obs, index) in creditInfo.observaciones" :key="index">{{ obs }}</li>
        </ul>
        <button class="button" @click="showAllInfo = false" id="vermenos">Ver menos</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    creditInfo: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      showAllInfo: false
    };
  }
};
</script>

<style>
.tarjeta-container {
  display: inline-block;
  padding: 20px;
}

.tarjeta {
  border-radius: 30px;
  border: 3px solid #ccc;
  padding: 10px;
  background-color: grey;
  color: white;
}

.button {
  position: relative;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
}

#vermas,
#vermenos {
  position: relative;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
}
</style>
