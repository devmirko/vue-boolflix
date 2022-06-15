<template>
<main>
    <div id="research">
        <input type="text" v-model="userSearch">
        <button @click="getList(); getListTv()">cerca</button>

    </div>

    <div class="container">

        <!-- film -->
        <div class="box_film">
            <div class="film" v-for="(element, i) in filteredlistFilm" :key="i">
                <div class="box_image">
                    <img :src="urlImage + element.backdrop_path" alt="">
                </div>


                <div class="card"></div>
                    <div class="title">{{ element.title }}</div>
                    <div class="original_title">{{ element.original_title }}</div>
                    <div class="lang">{{ element.original_language }}
                        <!-- se la bandiera e inglese -->
                        <span v-if="element.original_language === 'en'" class="flag"><img src="../assets/britain_inghilterra_icon.png" alt=""></span>
                        <!-- se la bandiera e italiana -->
                        <span v-else-if="element.original_language === 'it'" class="flag"><img src="../assets/flag_italy_icon.png" alt=""></span>
                    </div>
                <div class="vote">
                    <div v-if="getStars(element.vote_average) == 0">
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(element.vote_average) == 1">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(element.vote_average) == 2">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(element.vote_average) == 3">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(element.vote_average) == 4">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(element.vote_average) == 5">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                    </div>
                        
                 
                </div>
            </div>    
        </div>

        <!-- serie tv -->
         <div class="box_serie">
            <div class="serie" v-for="(element, i) in filteredlistTv" :key="i">
                <div class="box_image">
                    <img :src="urlImage + element.backdrop_path" alt="">
                </div>
                <div class="card"></div>
                    <div class="title">{{ element.name }}</div>
                    <div class="original_title">{{ element.original_name }}</div>
                    <div class="lang">{{ element.original_language }}
                        <!-- se la bandiera e inglese -->
                        <span v-if="element.original_language === 'en'" class="flag"><img src="../assets/britain_inghilterra_icon.png" alt=""></span>
                        <!-- se la bandiera e italiana -->
                        <span v-else-if="element.original_language === 'it'" class="flag"><img src="../assets/flag_italy_icon.png" alt=""></span>
                    </div>
                <div class="vote">
                    <div v-if="getStars(element.vote_average) == 0">
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(element.vote_average) == 1">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(element.vote_average) == 2">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(element.vote_average) == 3">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['far', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(element.vote_average) == 4">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['far', 'star']" />
                    </div>
                    <div v-else-if="getStars(element.vote_average) == 5">
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                        <fas :icon="['fas', 'star']" />
                    </div>
                        
                 
                </div>
            </div>    
        </div>



  </div>
</main>
</template>

<script>
import axios from "axios"

export default {
  name: 'MainApp',
  components: {
 

  },
  data(){
    return{
        apiUrl:"",
        apiUrlTv:"",
        listFilm : [],
        listSerieTv: [],
        userSearch: "",
        urlImage: "http://image.tmdb.org/t/p/w342/",
        
    }
  },

  methods: {
    // funzione che ricerca i film
    getList() {
        this.apiUrl = "https://api.themoviedb.org/3/search/movie?api_key=fd3f42d04d0da0ec874d9333f867384a&language=it-IT&query=" + this.userSearch,
        axios.get(this.apiUrl)
    .then((result) => {
        this.listFilm = result.data.results;
        console.log(result);
    })
    .catch((error)  => {
       console.log("errore", error);
    })
    },
    // funzione che ricerca le serie tv
     getListTv() {
        this.apiUrlTv = "https://api.themoviedb.org/3/search/tv?api_key=fd3f42d04d0da0ec874d9333f867384a&language=it-IT&query=" + this.userSearch,
        axios.get(this.apiUrlTv)
    .then((result) => {
        this.listSerieTv = result.data.results;
        console.log(result);
    })
    .catch((error)  => {
       console.log("errore", error);
    })
    },
    getStars(vote) {
      return Math.round(vote / 2);
    },
   
  

  },

  computed: {
    filteredlistFilm(){
          if (this.userSearch ==="") {
             return this.listFilm; 
        }  else {
       return this.listFilm.filter(card => {
            return card.title.toLowerCase().includes(this.userSearch.toLowerCase());
            
       });
        
    } 
  },

  filteredlistTv(){
    if (this.userSearch ==="") {
             return this.listSerieTv; 
        }  else {
       return this.listSerieTv.filter(item => {
            return item.name.toLowerCase().includes(this.userSearch.toLowerCase());
            
       });
        
    } 

  }

 

}

}


</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
main{
    background-color: rgb(69, 68, 68);

    #research{
        height: 50px;
        text-align: center;
        line-height: 50px;

        input{
            width: 180px;
           margin-right: 20px;
        }
        button{
          width: 50px;
          height: 20px;
        }

       
    }

    .container{
    width: 100%;
    height: calc(100vh - 120px);
    display: flex;
    flex-wrap: wrap;
    justify-content: center;



         .box_film{
            width: 100%;
            display: flex ;
            background-color: black;
            overflow-x: scroll;


               .film{
                width: calc(100% / 5 );
                // debugger
                color: white;

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
        }

        .box_serie{
            width: 100%;
            display: flex ;
            flex-wrap: nowrap;
            background-color: black;
            overflow-x: scroll;
            


               .serie{
                width: calc(100% / 5 );
                // debugger
                color: white;

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
        }



    }
}


</style>
