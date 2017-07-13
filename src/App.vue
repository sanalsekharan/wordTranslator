<template>
  <div class="well" id="app">
    <div class="Projectheader">
      <Projectheader></Projectheader>
    </div>
    <br>
    <TranslatorForm v-on:formSubmit="translateText" ></TranslatorForm >
      <br>
      <TranslatorOutput v-text="translatedText"></TranslatorOutput>

  </div>
</template>

<script>

import Projectheader from './components/Header'
import TranslatorForm  from './components/TranslatorForm'
import TranslatorOutput  from './components/TranslatorOutput'

export default {
  name: 'app',
  data:function () {
      return{
        translatedText:''
      }
  },
  components:
  {
    Projectheader,
    TranslatorForm,
    TranslatorOutput
  },
  methods:{
    translateText: function (text,lang) {
        this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20170713T034009Z.8f4730be2d4da3fe.33a01400006410c29b1f45087a6ebe7418c54e72&lang='+lang+'&text='+text).then((responce)=>{
          this.translatedText = responce.body.text[0];
        })
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
  padding-left: 400px;
    padding-right: 400px;
}
.Projectheader{
  background-color: cornflowerblue;
    padding: 17PX;
    color: white;
}
</style>
