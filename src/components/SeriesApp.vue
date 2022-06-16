<template>

    <div class="film">
        <div class="box_image" v-if="listObjectSeries.backdrop_path === null">
            <img src="../assets/no-image.jpg" alt="" class="poster">
            <div class="card">
                    <div class="title">{{ listObjectSeries.name }}</div>
                    <div class="original_title">{{ listObjectSeries.original_name }}</div>
                    <div class="lang">{{ listObjectSeries.original_language }}
                        <!-- se la bandiera e inglese -->
                        <span v-if="listObjectSeries.original_language === 'en'" ><img src="../assets/britain_inghilterra_icon.png" alt="" class="flag"></span>
                        <!-- se la bandiera e italiana -->
                        <span v-else-if="listObjectSeries.original_language === 'it'"><img src="../assets/flag_italy_icon.png" alt=""  class="flag"></span>
                    </div>

                    
                <div class="vote">
                    <div v-if="getStars(listObjectSeries.vote_average) == 0">
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(listObjectSeries.vote_average) == 1">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(listObjectSeries.vote_average) == 2">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(listObjectSeries.vote_average) == 3">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(listObjectSeries.vote_average) == 4">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(listObjectSeries.vote_average) == 5">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                    </div>
                        
                 
                </div>
                <!-- descrizione -->
                <div class="overview">{{ listObjectSeries.overview }}</div>
            </div>
        </div>
        <!-- se e presente l'immagine -->
        <div class="box_image" v-else >
            <img :src="urlImage + listObjectSeries.backdrop_path" alt="" class="poster">
            <div class="card">
                <div class="title">{{ listObjectSeries.name }}</div>
                <div class="original_title">{{ listObjectSeries.original_name }}</div>
                <div class="lang">{{ listObjectSeries.original_language }}
                        <!-- se la bandiera e inglese -->
                        <span v-if="listObjectSeries.original_language === 'en'" ><img src="../assets/britain_inghilterra_icon.png" alt="" class="flag"></span>
                        <!-- se la bandiera e italiana -->
                        <span v-else-if="listObjectSeries.original_language === 'it'"><img src="../assets/flag_italy_icon.png" alt="" class="flag"></span>
                </div>

                    
                <div class="vote">
                    <div v-if="getStars(listObjectSeries.vote_average) == 0">
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(listObjectSeries.vote_average) == 1">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(listObjectSeries.vote_average) == 2">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(listObjectSeries.vote_average) == 3">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(listObjectSeries.vote_average) == 4">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(listObjectSeries.vote_average) == 5">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                    </div>
                </div>
                <!-- descrizione -->
                <div class="overview">{{ listObjectSeries.overview }}</div>
            </div>
        </div>
    </div>    

   
</template>

<script>


export default {
  name: 'SeriesApp',
   props: {
   listObjectSeries: Object
    
   
 },
 data(){
    return{
        urlImage: "http://image.tmdb.org/t/p/w780/",
        
    }
  },

  methods:{
   getStars(vote) {
      return Math.round(vote / 2);
    },
  }
}

</script>

<style scoped lang="scss">
.film{
     min-width: 400px;
     height: 100%;
     
    
    .box_image{
        width:  100%;
        height: 100%;
        position: relative;

        .poster{
            width: 100%;
            height: 100%;
            position: absolute;
            z-index: 100;
            
             
         &:hover{
           opacity: 0;
            
            
         }

           
         }


         .card{
        width:  100%;
        height: 100%;
        position: absolute;
        top: 0;
        left: 0;
        z-index: 10;
        background-color: black;
        color: white;
        padding: 10px;
        

            //titolo
                        
            .title{
                width: 100%;
                margin-bottom: 20px;
                text-align: center;
                font-size: 20px;
                font-weight: 700;
            }

            .original_title{
                width: 100%;
                margin-bottom: 18px;
                text-align: center;
                font-size: 20px;
                font-weight: 700;
            }

            // lingua
            .lang{
                font-size: 40px;
                font-weight: 700;
                margin-bottom: 20px;
                width: 100%;
                display: flex;
                justify-content: space-around;
                align-content: center;

                span{
                    width: 10px;
                    height: 10px;

                    .flag{
                        min-width: 100%;
                        min-height: 100%;
                    }
                }

            }
            // overviw
            .overview{
                margin-top: 10px;
                font-size: 16px;
                font-weight: 500;

            }
       }


    }
    
}



</style>