<template>
  <main>


      


        
      

        
      

    <div class="films" >
      <h2 class="my-5" v-if="fullArrayFilm">FILM</h2> 

      <div v-for="film in filmList"
      :key="film.id">

        <div class="scene scene--card">
          <div
          class="card"
          @click="cardOne == 'start' ? (cardOne = 'flipped' ) : (cardOne = 'start' )"
          v-bind:class="{ flipme: cardOne == 'flipped' }"
          >


            <div class="card__face card__face--front">
        
              <h4>Titolo: {{film.title}}</h4>
              <h6>Titolo originale: {{film.original_title}}</h6>
              <img
              :src="`https://image.tmdb.org/t/p/w342/${film.poster_path}`" 
              :alt="film.title">
            
              <div>
                <p v-if="langArray.includes(film.original_language)"> Lingua: 
                  <img class="flag"
                  :src="require(`../assets/img/${film.original_language}.png`)" :alt="film.title">
                </p>
                
                <p v-else>Lingua: {{film.original_language}}</p>
              </div>
          
              <div>
                <p>

                  Voto: 
                  <i
                  v-for="(item, index) in 5" :key="index"
                  class="fa-star"
                  :class="index < Math.round(film.vote_average/2) ? 'fas' : 'far' ">
                </i>
              
                </p>
                
              </div>
            </div>

            <div class="card__face card__face--back">Trama: {{film.overview}}</div>


          </div>
        </div>
      </div>
    </div>
    











    <div class="series justify-content-center">

      <h2 class="my-5 container" v-if="fullArraySerie">SERIE</h2> 

      <div class=""
      v-for="serie in serieList"
      :key="serie.id"> 

        <div class="scene scene--card">
          <div
          class="card"
          @click="cardOne == 'start' ? (cardOne = 'flipped' ) : (cardOne = 'start' )"
          v-bind:class="{ flipme: cardOne == 'flipped' }"
          >


            <div class="card__face card__face--front">
        
              <h4>Titolo: {{serie.name}}</h4>
              <h6>Titolo originale: {{serie.original_name}}</h6>
              <img
              :src="`https://image.tmdb.org/t/p/w342/${serie.poster_path}`" 
              :alt="serie.title">

                <div>
                  <p v-if="langArray.includes(serie.original_language)"> Lingua: 
                    <img class="flag"
                    :src="require(`../assets/img/${serie.original_language}.png`)" :alt="serie.name">
                  </p>
                
                  <p v-else>Lingua: {{serie.original_language}}</p>
                </div>



                <div>
                <p>
                  Voto: 
                  <i
                  v-for="(item, index) in 5" :key="index"
                  class="fa-star"
                  :class="index < Math.round(serie.vote_average/2) ? 'fas' : 'far' ">
                  </i>
                </p>
                </div>
                
            </div>
            <div class="card__face card__face--back">Trama: {{serie.overview}}</div>

          </div>
        </div>
      </div>
    </div>
    
  </main>
</template>

<script>

//IMPORT COMPONENTS

export default {
  name: 'Main',
  props:{
    filmList: Array,
    serieList: Array,
    fullArrayFilm: Boolean,
    fullArraySerie: Boolean
  },

  data(){
    return{
      langArray: ['en', 'it'],
      cardOne: 'start'
      
    }
  }
}
</script>

<style lang="scss" scoped>

.series, .films{
  margin: 20px 10px;

  .flag{
    height: 20px;
    width: 30px;
  }
  img{
    width: 200px;
  }
}



.scene {
  width: 300px;
  height: 450px;
  border: 1px solid #ccc;
  margin: 40px;
  text-align: center;
  // padding: 20px;
  // perspective: 600px;
}

.card {
  width: 100%;
  height: 100%;
  transition: transform 1s;
  transform-style: preserve-3d;
  cursor: pointer;
  position: relative;
}

.card__face {
  position: absolute;
  width: 100%;
  height: 100%;

  color: black;


  backface-visibility: hidden;
}


.card__face--back {
  transform: rotateY(180deg);
}

/* this style is applied when the card is clicked */
.flipme {
  transform: rotateY(180deg);
}

</style>