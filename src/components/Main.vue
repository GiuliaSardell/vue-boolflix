<template>
  <main>

    <!-- voglio mettere film e serie visibili quando una variabile booleana è vera
    devo mettere la variabile = false, diventa true se l'array non è vuoto-->
    <div class="films" >
      <h2 class="my-5" v-if="fullArrayFilm">FILM</h2> 

      <div v-for="film in filmList"
      :key="film.id">
      
      <h4>Titolo: {{film.title}}</h4>
      <h6>Titolo originale: {{film.original_title}}</h6>
      <img
      :src="`https://image.tmdb.org/t/p/w342/${film.poster_path}`" 
      :alt="film.title">
     

      <!-- <h6>Lingua: {{film.original_language}}</h6> -->
      <!-- <h6 v-if="film.original_language === 'en'">
        Lingua: <img src="../assets/img/it.png" alt="">
      </h6> -->
      <!-- <h6 v-if="langArray.includes('en')">
        Lingua: <img  :src="`../assets/img/${film.original_language}.png`" :alt="`${film.original_language}`">
      </h6>
      <h6 v-else>
        Lingua: {{film.original_language}}
      </h6> -->
      <div>
        <p v-if="langArray.includes(film.original_language)"> Lingua: 
          <img class="flag"
          :src="require(`../assets/img/${film.original_language}.png`)" :alt="film.title">
        </p>
        
        <p v-else>Lingua: {{film.original_language}}</p>
      </div>
      
      <!-- <h6>Voto: {{film.vote_average}} -> {{math.round(film.vote_average/2)}} </h6>  -->
      <h6>Voto: {{Math.round(film.vote_average/2)}}</h6>

  
      <div>
        <i
        v-for="(item, index) in 5" :key="index"
        class="fa-star"
        :class="index < Math.round(film.vote_average/2) ? 'fas' : 'far' ">
        </i>
       
  
      </div>


    
      </div>
    </div>
    

    <div class="series justify-content-center">

      <h2 class="my-5 container">SERIE</h2> 

      <div class=""
      v-for="serie in serieList"
      :key="serie.id"> 
      
        <h4>Titolo: {{serie.name}}</h4>
        <h6>Titolo originale: {{serie.original_name}}</h6>
        <!-- <h6>Lingua: {{film.original_language}}</h6> -->
        <h6 v-if="serie.original_language === 'en'">
          Lingua: <img src="../assets/img/it.png" alt="">
        </h6>
        <h6 v-else-if="serie.original_language === 'it'">
          Lingua: <img src="../assets/img/en.png" alt="">
        </h6>
        <h6 v-else>
          Lingua: {{serie.original_language}}
        </h6>
        <h6>Voto: {{serie.vote_average}}</h6>
    
      </div>
    </div>
    
    <Card />
  </main>
</template>

<script>

//IMPORT COMPONENTS
import Card from "./Card.vue"

export default {
  name: 'Main',
  props:{
    filmList: Array,
    serieList: Array,
    fullArrayFilm: Boolean,
    fullArraySerie: Boolean
  },
  components:{
    Card
  },
  data(){
    return{
      langArray: ['en', 'it']
      
    }
  }
}
</script>

<style lang="scss" scoped>

.series, .films{
  margin: 20px 10px;
  h4{
    margin-top: 50px;
  }
  .flag{
    height: 20px;
    width: 30px;
  }
  img{
    width: 200px;
    margin: 10px 0;
  }
}

</style>