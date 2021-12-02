<template>
  <main>

    <div v-for="film in filmList"
    :key="film.id"> 
      <h4>Titolo: {{film.title}}</h4>
      <h6>Titolo originale: {{film.original_title}}</h6>
      <!-- <h6>Lingua: {{film.original_language}}</h6> -->
      <h6 v-if="film.original_language === 'en'">
        <img src="../assets/img/it.png" alt="">
      </h6>
      <h6 v-else-if="film.original_language === 'it'">
        <img src="../assets/img/en.png" alt="">
      </h6>
      <h6 v-else>
        {{film.original_language}}
      </h6>
      <h6>Voto: {{film.vote_average}}</h6>
    
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
    filmList: Array
  },
  components:{
    Card
  }
}
</script>

<style lang="scss" scoped>




div{
  margin: 20px 10px;
}

</style>