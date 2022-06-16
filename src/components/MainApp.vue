<template>
<main>
    <div id="research">
      <div class="container_input">
        <input type="text" v-model="userSearch" @keyup.enter="getList(); getListTv()">
        <button @click="getList(); getListTv()" class="fill">
        <!-- svg -->
         <svg aria-hidden='true' viewBox='0 0 24 24'>
            <path d='M9.5,3A6.5,6.5 0 0,1 16,9.5C16,11.11 15.41,12.59 14.44,13.73L14.71,14H15.5L20.5,19L19,20.5L14,15.5V14.71L13.73,14.44C12.59,15.41 11.11,16 9.5,16A6.5,6.5 0 0,1 3,9.5A6.5,6.5 0 0,1 9.5,3M9.5,5C7,5 5,7 5,9.5C5,12 7,14 9.5,14C12,14 14,12 14,9.5C14,7 12,5 9.5,5Z' />
          </svg>
        </button>
      </div>
    </div>

    <div class="container">
        <div class="genere_film"><h3>FILM</h3></div>
        <div class="genere_serie"><h3>SERIE TV</h3></div>

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
        display: flex;
        align-items: center;
        justify-content: end;

      .container_input{
        display: flex;
        margin-right: 20px;


        input{
          border: 1px solid rgba(0, 0, 0, 0.54);
          width: 100%;
          padding: 8px;
          font-size: 16px;
          line-height: 1.5;
          flex: 1;

        
         
        }
        // button
        button{
         border: 1px solid red;
         padding: 8px 16px;
         background: red ;
         display: flex;
         align-items: center;
         justify-content: center;
         cursor: pointer;

             svg{
              width: 24px;
              height: 24px;
              
             }

      
        }




      }

        
       
    }

    .container{
    width: 100%;
    height: calc(100vh - 120px);
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    position: relative;
         .genere_film{
          width: 200px;
          height: 40px;
          background-color: rgba(255, 0, 0, 0.333);
          position: absolute;
          top: 20px;
          left: 20px;
          z-index: 20;
          display: flex;
          align-items: center;
          justify-content: center;
         }

         .genere_serie{
          width: 200px;
          height: 40px;
          background-color: rgba(255, 0, 0, 0.333);
          position: absolute;
          bottom: 500px;
          left: 20px;
          z-index: 20;
          display: flex;
          align-items: center;
          justify-content: center;
         }



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
