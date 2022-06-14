<template>
<main>
    <div id="research">

    </div>
    <div class="container">
        <div class="box_film">
            <div class="film">
                <div class="title"></div>
                <div class="original_title"></div>
                <div class="lang"></div>
                <div class="vote"></div>
            </div>
        </div>
    </div>
</main>
</template>

<script>
import axios from "axios"

export default {
  name: 'Main',
  components: {
 

  },
  data(){
    return{
        apiUrl:"https://api.themoviedb.org/3/search/movie?api_key=fd3f42d04d0da0ec874d9333f867384a&language=it-IT&query=The+Wolf+of+Wall+Street&page=1&include_adult=true",
        listFilm : [],
        userSearch: "",
    }
  },
  created(){
      this.getList();
  },
  methods: {
    getList() {
        axios.get(this.apiUrl)
    .then((result) => {
        this.listFilm = result.data.results;
        console.log(result);
    })
    .catch((error)  => {
       console.log("errore", error);
    })
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
    }

    .container{
    width: 100%;
    height: calc(100vh - 120px);
    display: flex;
    justify-content: center;


         .box_film{
            width: 80%;
            display: flex;
            align-content: center;
            flex-wrap: wrap;
            background-color: black;
         }
    }
}


</style>
