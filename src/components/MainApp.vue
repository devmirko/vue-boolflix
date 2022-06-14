<template>
<main>
    <div id="research">
        <input type="text" v-model="userSearch">
        <button @click="getList">cerca</button>

    </div>
    <div class="container">
        <div class="box_film">
            <div class="film" v-for="(element, i) in filteredlistFilm" :key="i">
                <div class="title">{{ element.title }}</div>
                <div class="original_title">{{ element.original_title }}</div>
                <div class="lang">{{ element.original_language }}</div>
                <div class="vote">{{ element.vote_average }}</div>
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
        api_key: "fd3f42d04d0da0ec874d9333f867384a",
        apiUrl:"",
        listFilm : [],
        userSearch: "",
    }
  },

  methods: {
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
    }
  

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
    justify-content: center;


         .box_film{
            width: 80%;
            display: flex ;
            flex-wrap: wrap;
            background-color: black;


               .film{
                width: calc(100% / 5 );
                // debugger
                color: white;
               }
         }
    }
}


</style>
