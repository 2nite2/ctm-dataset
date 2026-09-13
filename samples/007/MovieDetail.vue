<template>
  <div class="movie-detail">
        <h2>{{movie.Title}}</h2>
    <div class="container">
        <div class="poster">
            <img :src="movie.Poster" alt="Movie Poster" class="featured-img" />
        </div>
        <div class="detail">
            <p>{{ movie.Plot }}</p>
            <p><b>Genre :</b> {{ movie.Genre }}</p>
            <p><b>Year :</b> {{ movie.Year }}</p>
            <p><b>Language :</b> {{ movie.Language }}</p>
            <p><b>Awards :</b> {{ movie.Awards }}</p>
            <p><b>Actors :</b> {{ movie.Actors }}</p>
            <p><b>totalSeasons :</b> {{ movie.totalSeasons }}</p>
            <p><b>imdbRating :</b> {{ movie.imdbRating }}</p>

        </div>
    </div>
  </div>
</template>

<script>
import {ref, onBeforeMount} from 'vue';
import { useRoute } from 'vue-router';
import env from "@/env.js";
export default {
    setup(){
        const movie = ref({});
        const route = useRoute();

        onBeforeMount(() => {
            fetch(`https://www.omdbapi.com/?apikey=${env.apikey}&i=${route.params.id}&plot=full`)
            .then(response => response.json())
            .then(data => {
                console.log(data);
                movie.value = data;
            })
        });

        return {
            movie
        }
    }
}
</script>

<style lang="scss">
.movie-detail {
  padding: 16px;
  h2 {
    color: #FFF;
    font-size: 28px;
    font-weight: 600;
    margin-bottom: 16px;
  }
  .featured-img {
    display: block;
    max-width: 200px;
    margin-bottom: 16px;
  }
  p {
    color: #FFF;
    font-size: 18px;
    line-height: 1.4;
  }

   h2{
        text-align: center;
    }

  .container{
    width: 80%;
    margin: 0 auto;
    display: flex;
    .detail{
        padding: 0px 0px 0px 10px;

        p:not(:first-child){
            padding-top: 2%;
        }
    }
   
  }
}
</style>