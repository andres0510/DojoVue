<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>traductor</h1>
    <translateIn v-on:formSubmit="traducirTexto"></translateIn>
    <translateOut v-text="traducirEsteTexto"></translateOut>
  </div>
</template>

<script>
import translateIn from './components/translateIn.vue'
import translateOut from './components/translateOut.vue'

export default {
  name: 'app',
  components: {
    translateIn,
    translateOut
  },
  data: function(){
    return{
      traducirEsteTexto:''
    }
  },
  methods:{
    traducirTexto: function(texto, idioma){
      this.$http.get(`https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190622T213455Z.f67e95598c7aee64.c0c49d0594aa527178d83c8e3c1a81ed05709a56&lang=${idioma}&text=${texto}`)
      .then((response)=>{
        this.traducirEsteTexto = response.body.text[0];
      });
    }
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
  margin-top: 60px;
}
</style>
