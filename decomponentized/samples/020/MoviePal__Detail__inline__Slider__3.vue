<script setup>
import { onMounted, watch } from 'vue'
import { useRoute, useRouter } from 'vue-router'
import { Mousewheel, Navigation, Autoplay, Parallax, A11y } from 'swiper'
import { Swiper, SwiperSlide } from 'swiper/vue'
import { ImagePath } from '@/utils/index.js'
import Detail from '@/components/Detail.vue'
import Slider from '@/components/Slider.vue'
import Loading from '@/components/Loading.vue'
import { useMovieStore } from '@/stores/index'

const movieStore = useMovieStore()
const route = useRoute()
const router = useRouter()
const SwiperModules = [Navigation, Mousewheel, Autoplay, Parallax, A11y]

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

function moviesDetailGo(id, click) {
  if (click) {
    router.push({ name: 'Detail', params: { id } })
  }
}
</script>

<template>
  <div class="detail">
    <Loading> </Loading>
    <Detail :movieDetail="movieStore.movieDetail"></Detail>

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

      <div class="container" v-if="movieStore.creditsDetail.cast">
          <Swiper :modules="SwiperModules" :slides-per-view="3" :space-between="40" :navigation="true" :mousewheel="true"
            :autoHeight="true" :parallax="true" :lazy="true">
            <SwiperSlide v-for="item in movieStore.creditsDetail.cast" :key="item">
              <div class="carousel__item">
                <div class="card border-0" @click="moviesDetailGo(item.id, castFields.clickable)">
                  <img v-if="castFields.imagePath" loading="lazy" :src="ImagePath(item[castFields.imagePath])"
                    class="rounded-3" alt="Picture">
                  <div class="swiper-lazy-preloader swiper-lazy-preloader-white"></div>
                  <div class="card-itemc cast-slider">
                    <h5 class="card-title text-truncate fw-bold" v-if="castFields.title">{{ item[castFields.title] }}</h5>
                    <div class="d-flex justify-content-between align-items-center">
                      <small class="text-muted" v-if="castFields.profession">{{ item[castFields.profession] }}</small>
                      <span class="badge bg-warning mx-1" v-if="castFields.vote">{{ Number(item[castFields.vote]).toFixed(2) }}
                      </span>

                    </div>
                  </div>
                </div>
              </div>
            </SwiperSlide>
          </Swiper>
        </div>

      <h3 class="mt-5">{{ $t("Producer") }}</h3>

      <Slider :sliderData="movieStore.creditsDetail.crew" :customFields="crewFields"></Slider>
    </div>
  </div>
</template>


<style scoped>
.cast-slider {
  display: flex;
  flex-wrap: wrap;
  align-content: center;
  justify-content: center;
  align-items: center;
  flex-direction: column
}
</style>
