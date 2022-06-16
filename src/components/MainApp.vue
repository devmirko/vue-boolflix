<template>
<main>
    <div id="research">
        <input type="text" v-model="userSearch">
        <button @click="getList(); getListTv()">cerca</button>

    </div>

    <div class="container">

        <!-- film -->
        <div class="box_film">
            <FilmApp v-for="(element, i) in filteredlistFilm" :key="i"
            :listObjectFilm ="element"/>
        
        </div>
        <!-- serie tv -->
         <div class="box_serie">
            <SeriesApp v-for="(element, i) in filteredlistTv" :key="i"
            :listObjectSeries ="element"/>
        </div>



  </div>
</main>
</template>

<script>
import axios from "axios"
import FilmApp from './FilmApp.vue'
import SeriesApp from './SeriesApp.vue'


export default {
  name: 'MainApp',
  components: {
    FilmApp,
    SeriesApp,
   
 

  },
  data(){
    return{
        apiUrl:"",
        apiUrlTv:"",
        listFilm : [],
        listSerieTv: [],
        userSearch: "",
        
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
            height: 50%;
            display: flex ;
            background-color: black;
            overflow-x: scroll;

        }

        .box_serie{
            width: 100%;
            height: 50%;
            display: flex ;
            flex-wrap: nowrap;
            background-color: black;
            overflow-x: scroll;
            
        }



    }
}


</style>
