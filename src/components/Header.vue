<template>
  <header>
    <h2>BOOLFIX</h2>

    <div class="container-input">
      <input 
      type="text" 
      class="form-control" 
      placeholder="Cerca un film..."
      v-model="textInput"
      @keyup.enter="checkValidSearch"
      >

      <button 
      type="button" 
      class="btn"
      @click="checkValidSearch"
      >
      Cerca
      </button>
    </div>

    

  </header>
</template>

<script>

//IMPORT COMPONENTS



export default {
  name: 'Header',

  data() {
    return {
      textInput: '',
    }
  },
  methods:{
    checkValidSearch() {
      if (this.textInput !== '') {
        
        this.$emit('sendSearch', this.textInput);
        console.log('emit');
      } else {
        alert('Attenzione!\nInserisci il titolo di un film')
      }
    }
  }

}
</script>

<style lang="scss">
//IMPORT
@import "../assets/style/mixin.scss";

header{
  height: 80px;
  background-color: black;
  @include center();
  h2{
    color: red;
    margin: 0 10px;
  }
  
  .container-input{
    display: flex;
    input{
    width: 300px !important;
    margin: 0 10px !important;
    }
    button{
      background-color: red;
      color: white;
      margin: 0 10px;
    }
  }
}

</style>