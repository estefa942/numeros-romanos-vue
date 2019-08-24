<template>
  <div id="app">
    <h1 class="title">CONVERSOR DE NUMEROS DECIMALES A NUMEROS ROMANOS</h1>
    <div>
      <input class="input-number" v-model="number" type="number"/>
      <button type="button" class="button-send" v-on:click="toRomano">Convertir</button>
    </div>

    <div>
      <p>{{salida}}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      number:'',
      salida: "",
      decimal: [1, 4, 5, 9, 10, 40, 50, 90, 100, 400, 500, 900, 1000],
      romano: ["I","IV","V","IX","X","XL","L","XC","C","CD","D","CM","M"]
    };
  },
  methods: {
    toRomano() {
      let number = this.number;
      this.number='';
      this.salida = '';
      let i;
      for (i = 12; i >= 0; i--) {
        while (number >= this.decimal[i]) {
          number = number - this.decimal[i];
          this.salida = this.salida + this.romano[i];
        }
      }
    }
  }
};
</script>

<style>
#app {
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.input-number{
    width: 400px;
    height: 30px;
    border-radius: 15px;
    border-color: violet;
    text-align: center;
}

.button-send{
    height: 30px;
    border-radius: 15px;
    background-color: greenyellow;
    width: 150px;
}

p{
  font-size: -webkit-xxx-large;
}
</style>
