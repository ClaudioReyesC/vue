<template>
  <div class="form">
    <h1>Simulador credito Hipotecarios</h1>
    <h2 id="title">Ingrese los Datos</h2>
    <div>
      <label id="valorPropiedad1" for="valorPropiedad">Valor Propiedad (UF):</label>
      <input type="number" id="valorPropiedad" v-model="valorPropiedad">
    </div>
    <div>
      <label for="pie" id="pie1">Pie (UF):</label>
      <input type="number" id="pie" v-model="pie">
    </div>
    <div>
      <label for="tasaInteres" id="tasaInteres1">Tasa de Interés (%):</label>
      <input type="number" id="tasaInteres" v-model="tasaInteres" placeholder="5">
    </div>
    <div>
      <label for="plazo" id="plazo1">Plazo (años):</label>
      <input type="number" id="plazo" v-model="plazo">
    </div>
    <button class="my-button" @click="emitirCalculo">Calcular</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      valorPropiedad: null,
      pie: null,
      tasaInteres: 5, // Por defecto 5%
      plazo: null,
    };
  },
  methods: {
    emitirCalculo() {
      this.$emit('calcular', {
        valorPropiedad: this.valorPropiedad,
        pie: this.pie,
        tasaInteres: this.tasaInteres,
        plazo: this.plazo
      });
    }
  }
};
</script>
<style>
.form {
  background-image: url(https://brokersfinancieros.com.mx/wp-content/uploads/2021/06/Pasos-Cre%CC%81dito-Hipotecario-Portada-HD.jpg);
  width: 100%;
  height: 80vh;
  background-size: cover;


}



.my-button {
  padding: 10px 20px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  position: relative;
  bottom: ;
  top: 50px;
  left: 45%;
}

.my-button:hover {
  background-color: #45a049;
}

.my-button:active {
  background-color: #3e8e41;
}

h1 {
  color: white;
  text-align: center;
}

#title {
  color: white;
  font-style: italic;
  padding: 2px;
  position: relative;
  display: inline;
  text-align: center;
  left: 38%;
}

#valorPropiedad1 {
  font-style: italic;
  color: white;
  position: relative;
  top: 20px;
  left: 55%;
  margin: 10px
}

#valorPropiedad {
  font-style: italic;
  color: black;
  position: relative;
  top: 20px;
  left: 55%;
  margin: 10px
}

#pie1 {
  color: white;
  position: relative;
  top: 20px;
  left: 55%;
  margin: 10px
}

#pie {
  color: black;
  position: relative;
  top: 20px;
  left: 55%;
  margin: 10px
}

#tasaInteres1 {
  color: white;
  position: relative;
  top: 10px;
  left: 55%;
  margin: 10px
}

#tasaInteres {
  color: black;
  position: relative;
  top: 10px;
  left: 55%;
  margin: 10px
}

#plazo1 {
  color: white;
  position: relative;
  top: 20px;
  left: 55%;
  margin: 10px
}

#plazo {
  color: black;
  position: relative;
  top: 20px;
  left: 55%;
  margin: 10px
}
</style>