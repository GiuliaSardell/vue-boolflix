<template>
  <div id="app">
    <Header @sendSearch="performSearch" />
    <Main :filmList='films'/>
  </div>
</template>

<script>

//IMPORT COMPONENTS
import Header from "./components/Header.vue"
import Main from "./components/Main.vue"
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Header,
    Main
  },
  data() {
    return{
      textInput: "",
      films: [],
      generalUrl: 'https://api.themoviedb.org/3/search/movie?',
      myKey: 'api_key=5bb76975e29ce4ec5d24abbc5f794e87',
      query: '&query=ritorno al futuro',
      language: '&language=it-IT',
      
      
    }
  },
  methods:{
    performSearch(text){
      this.textInput = text;
      this.getApi();
    },
    getApi(){
      // this.isLoading = true;
      axios.get(`${this.generalUrl}${this.myKey}&query=${this.textInput}${this.language}`)
      .then(r =>{
        
        // this.isLoading = false;
  
        console.log('r',r)
        console.log('r.data.results',r.data.results)
        this.films = r.data.results;
        console.log('films array',this.films)
        console.log('textInput',this.textInput)
        
       
      })
      .catch( e => {
        console.log(e);
      })
    }
  }
  

}
</script>

<style lang="scss">
//IMPORT
@import "~bootstrap/scss/bootstrap.scss";





</style>
