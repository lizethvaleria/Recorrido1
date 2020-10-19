<template>
  <div id="app">
   
    <Escena
      class="w-50"
      :cielo="localizacionActual.cielo"
      :navegadores="localizacionActual.navegadores"
      :cielos="cielos"
      @cambiar="cambiar"
      :video="localizacionActual.video"
      :informacion="localizacionActual.informacion"
    />
  </div>
</template>

<script>
import Escena from "./components/Escena.vue";
const cielos = ["huella.jpg", "vistafrontal.jpg"];

const escenas = {
  huella: {
    cielo: "huella.jpg",
    navegadores: [{ posicion: "-9 -3 0", hacia: "vistafrontal" }],
  },
  vistafrontal: {
    cielo: "vistafrontal.jpg",
    navegadores: [{ posicion: "-9 -3 0", hacia: "huella" }],
    whatsapp: { posicion: "4 0 8" },
    video: { posicion: "-7.78 -1.01 6.6", link: "youtube.com" },
    informacion: { posicion: "-10.0 -2.23 10.4", link: "https://www.uanl.mx/"}
  },
}; 

export default {
  name: "App",
  data() {
    return {
      localizacionActual: escenas.huella,
      cielos: cielos,
    };
  },
  components: { Escena },
  methods: {
    cambiar: function (hacia) {
      this.localizacionActual = escenas[hacia];
    },
  },
  mounted() {},
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>