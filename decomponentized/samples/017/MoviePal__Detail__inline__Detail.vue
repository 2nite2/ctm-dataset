<script setup>
import { onMounted, watch } from 'vue'
import { useRoute } from 'vue-router'
import { ImagePath } from '@/utils/index.js'

import Slider from '@/components/Slider.vue'
import Loading from '@/components/Loading.vue'
import { useMovieStore } from '@/stores/index'

const movieStore = useMovieStore()
const route = useRoute()

const castFields = {
  imagePath: "profile_path",
  title: "name",
  profession: "character",
}
const crewFields = {
  imagePath: "profile_path",
  title: "name",
  profession: "job",
}

const recommendationsFields = {
  imagePath: "poster_path",
  title: "title",
  profession: "",
  clickable: "true",
  vote: "vote_average",
}

onMounted(() => {
  updateMovieDetail()
})

watch(() => route.params, () => {
  updateMovieDetail()
})

async function updateMovieDetail() {
  movieStore.getMovieDetail(route.params.id)
  movieStore.getCreditsDetail(route.params.id)
  await movieStore.getMovieRecommendations(route.params.id)
  if (movieStore.recommendationsDetail.length < 1) {
    movieStore.getSimilarMovies(route.params.id)
  }
}

function getDateYear(date) {
  if (date) {
    return `(${date.split('-')[0]})`
  }
  return ''
}
</script>

<template>
  <div class="detail">
    <Loading> </Loading>
    <div class="container">
        <div class="row mt-5 mb-5">
          <div class="card mb-4 border-0">
            <div class="row g-0">
              <div class="col-md-3 mt-1 mb-1 justify-content-center">
                <img :src="ImagePath(movieStore.movieDetail.poster_path)" class="img-fluid rounded" alt="..." loading="lazy" />
              </div>
              <div class="col-md-8">
                <div class="card-body">
                  <h5 class="card-title">{{ movieStore.movieDetail.title }} {{ getDateYear(movieStore.movieDetail.release_date) }}</h5>
                  <div class="col" v-if="movieStore.movieDetail.genres">
                    <span v-for="(item, index) of movieStore.movieDetail.genres" :key="index" class="badge bg-secondary mx-1">{{ item.name }}</span>
                  </div>
                  <span class="badge bg-warning mx-1">{{ Number(movieStore.movieDetail.vote_average).toFixed(2) }}</span>

                  <p class="card-text mx-1 mb-1 mt-1">{{ movieStore.movieDetail.overview }}</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

    <div class="container">
      <template v-if="movieStore.recommendationsDetail.length > 1">
        <h3>{{ $t("Recommendations") }}</h3>
        <Slider :sliderData="movieStore.recommendationsDetail" :customFields="recommendationsFields"></Slider>
      </template>

      <template v-else>
        <h3>{{ $t("SimilarMovies") }}</h3>

        <Slider :sliderData="movieStore.similarMovies" :customFields="recommendationsFields"></Slider>
      </template>



      <h3>{{ $t("Cast") }}</h3>

      <Slider :sliderData="movieStore.creditsDetail.cast" :customFields="castFields"></Slider>

      <h3 class="mt-5">{{ $t("Producer") }}</h3>

      <Slider :sliderData="movieStore.creditsDetail.crew" :customFields="crewFields"></Slider>
    </div>
  </div>
</template>
