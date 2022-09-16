<template>
  <div class="rowpost">
    <h2>{{title? title : ''}}</h2>
    <div class="posters">
      <div :key="index" v-for="(movie, index) in movies">
        <img :class="isSmall? 'small-poster' : 'poster'" @click="$router.push(`details/${movie.id}`)" :src="movie? imageUrl+ movie.backdrop_path : ''" alt="Poster"/>
      </div>
    </div>
  </div>
</template>

<script>
import axios from '../axios'
import { imageUrl } from '../constants/constants'

export default {
  name: 'RowPosts',
  data () {
    return {
      movies: [],
      imageUrl
    }
  },
  props: {
    isSmall: {
      required: false,
      default: '',
      type: String
    },
    title: {
      required: true,
      default: '',
      type: String
    },
    url: {
      required: true,
      default: '',
      type: String
    }
  },
  mounted () {
    axios.get(this.url)
      .then((response) => {
        this.movies = response.data.results
      })
  }
}
</script>

<style scoped>
  .rowpost{
      margin-left: 10px;
      margin-right: 10px;
      color: #fff;
      margin-top: 15px;
      font-size: 0.8rem;
  }
  .posters{
      display: flex;
      padding: 20px;
      overflow-x: scroll;
      overflow-y: hidden;
  }
  .posters::-webkit-scrollbar {
      display: none;
  }
  .poster{
      max-height: 250px;
      margin-right: 10px;
      cursor: pointer;
  }
  .small-poster{
      max-height: 150px;
      margin-right: 10px;
      cursor: pointer;
  }
  .poster:hover, .small-poster:hover{
      transform: scale(1.1);
  }

</style>
