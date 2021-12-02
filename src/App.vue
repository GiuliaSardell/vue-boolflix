<template>
  <div id="app">
    <Header @sendSearch="performSearch" />
    <Main 
    :filmList='films'
    :serieList='series'
    :fullArrayFilm= 'fullArrayFilm'
    :fullArraySerie= 'fullArraySerie'
    />
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
      series: [],
      fullArrayFilm: false,
      fullArraySerie: false,
      typeInput: "",
      movie: 'movie?',
      tv: 'tv?',
      generalUrl: 'https://api.themoviedb.org/3/search/',
      myKey: 'api_key=5bb76975e29ce4ec5d24abbc5f794e87',
      // query: '&query=ritorno al futuro',
      language: '&language=it-IT',

      
    }
  },
  methods:{
    performSearch(text){
      this.textInput = text;
      this.getApi();
    },
    getApi(){
    
      axios.get(`${this.generalUrl}${this.movie}${this.myKey}&query=${this.textInput}${this.language}`)
      .then(r =>{
        console.log('r movie',r)
        console.log('r.data.results movie',r.data.results)
        this.films = r.data.results;
        if(this.films != ''){
          this.fullArrayFilm = true;
        }
        
        console.log('films array movie',this.films)
        console.log('textInput',this.textInput)
      })
      .catch( e => {
        console.log(e);
      })


      axios.get(`${this.generalUrl}${this.tv}${this.myKey}&query=${this.textInput}${this.language}`)
      .then(r =>{
        console.log('r series',r)
        console.log('r.data.results series',r.data.results)
        this.series = r.data.results;
        if(this.series != ''){
          this.fullArraySerie= true
        }
        console.log('series array tv',this.series)
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
