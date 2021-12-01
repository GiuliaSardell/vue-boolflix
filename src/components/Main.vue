<template>
  <main>

    <div v-for="film in filmList"
    :key="film.key"> 
      <h4>Titolo: {{film.title}}</h4>
      <h6>Titolo originale: {{film.original_title}}</h6>
      <h6>Lingua: {{film.original_language}}</h6>
      <h6>Voto: {{film.vote_average}}</h6>
    
    </div>

  </main>
</template>

<script>
export default {
  name: 'Main',
  props:{
    filmList: Array
  }
}
</script>

<style lang="scss" scoped>
div{
  margin: 20px 10px;
}

</style>