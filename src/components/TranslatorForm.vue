<template>
  <div class="row" id="translator">
    <form class="well" v-on:submit ="formSubmit">
      <input class="form-control" type="text"  v-model ="textToTranslate" placeholder ="Enter words">
      <select class="form-control" v-model = "language">
        <option value="ml">Malayalam</option>
        <option value="hi">Hindi</option>
        <option value="ta">Tamil</option>
        <option value="ja">Japanese</option>

      </select>
      <br>
      <input class = "btn rtn-primary" type="submit" value="Translate">
    </form>
  </div>
</template>

<script>
export default {
  name: 'TranslatorForm',
  data(){
    return{
      textToTranslate:'',
      language: ''
    }
  },
  created (){
    this.language ='ml'
  },
  methods:{
    formSubmit(e) {
      this.$emit('formSubmit', this.textToTranslate,this.language);
      e.preventDefault();
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
