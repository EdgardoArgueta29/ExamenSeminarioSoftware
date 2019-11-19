<template>
  <div id="app" class="nt-3">
    <h5>Selección de moneda</h5>
    <form action="">
      <select name="" id="" @change="MonedaSeleccionada" v-model="moneda" class="form-control">
        <option value="USD">Dolar Americano</option>
        <option value="AUD">Dolar Australiano</option>
        <option value="CAD">Dolar Canadiense</option>
        <option value="EUR">Euro</option>
        <option value="GBP">Libra Esterlina</option>
      </select>
      <br>

      <select name="" id="2" @change="NuevaMonedaSeleccionada"  class="form-control">
        <option value="USD">Dolar Americano</option>
        <option value="AUD">Dolar Australiano</option>
        <option value="CAD">Dolar Canadiense</option>
        <option value="EUR">Euro</option>
        <option value="GBP">Libra Esterlina</option>
      </select>
    </form>
    <br>
    <br>
    <input type="text">
    <br>
    <br>
    <input type="text">
    <br>
<!--      <par v-for="(valor, codigo) in this.intercambios"-->
<!--           class="col-2"-->
<!--           :moneda="codigo"-->
<!--           :intercambio="valor"/>-->
  </div>
</template>

<script>


  import axios from 'axios'


  export default {
    name: "App",
    // components: {
    //   Par
    // },
    data: function () {
      return {
        moneda: '',
        intercambios: {}
      }
    },
    methods: {
      MonedaSeleccionada() {
        axios.get(`https://api.exchangerate-api.com/v4/latest/${this.moneda}`)
                .then((res) => {
                  this.intercambios = res.data.rates;
                })
      },
    },
    mounted() {
      if (this.moneda) {
        this.MonedaSeleccionada()
      }
      // else {
      //   console.log('La moneda no tiene valor')
      // }
    }
  }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }

  #nav {
    padding: 30px;
  }

  #nav a {
    font-weight: bold;
    color: #2c3e50;
  }

  #nav a.router-link-exact-active {
    color: #42b983;
  }
</style>
