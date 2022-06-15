<template>

            <div class="film">
                <div class="box_image">
                    <img :src="urlImage + listObjectFilm.backdrop_path" alt="">
                </div>


                <div class="card"></div>
                    <div class="title">{{ listObjectFilm.title }}</div>
                    <div class="original_title">{{ listObjectFilm.original_title }}</div>
                    <div class="lang">{{ listObjectFilm.original_language }}
                        <!-- se la bandiera e inglese -->
                        <span v-if="listObjectFilm.original_language === 'en'" class="flag"><img src="../assets/britain_inghilterra_icon.png" alt=""></span>
                        <!-- se la bandiera e italiana -->
                        <span v-else-if="listObjectFilm.original_language === 'it'" class="flag"><img src="../assets/flag_italy_icon.png" alt=""></span>
                    </div>

                    
                <div class="vote">
                    <div v-if="getStars(listObjectFilm.vote_average) == 0">
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(listObjectFilm.vote_average) == 1">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(listObjectFilm.vote_average) == 2">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(listObjectFilm.vote_average) == 3">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(listObjectFilm.vote_average) == 4">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(listObjectFilm.vote_average) == 5">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                    </div>
                        
                 
                </div>
            </div>    

   
</template>

<script>


export default {
  name: 'FilmApp',
   props: {
    listObjectFilm : Object
   
 },
 data(){
    return{
        urlImage: "http://image.tmdb.org/t/p/w342/",
        
    }
  },

  methods:{
   getStars(vote) {
      return Math.round(vote / 2);
    },
  }
}

</script>

<style lang="scss">
 .film{
     width: calc(100% / 5 );
    // debugger
    color: white;

    // bandiera
    .flag{
        display: inline-block;
        width: 20px;
        height: 20px;

        img{
        max-width: 100%;
        max-height: 100%;
        }
                   
    }
 }



</style>
