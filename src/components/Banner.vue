<template>
  <div :style="{ backgroundImage: `url(${movie? imageUrl+ movie.backdrop_path : ''})` }" class='banner'>
    <div class='content'>
      <h1 class='title'>{{ movie.title? movie.title : movie.name }}</h1>
      <div class='banner-buttons'>
          <button class='banner-btn'>Play</button>
          <button class='banner-btn'>My List</button>
      </div>
      <h3 class='description'>{{movie ? movie.overview.substring(0, maxOverview)+'...' : ''}}</h3>
    </div>
    <div class="fade-bottom"></div>
  </div>
</template>

<script>
import axios from '../axios'
import { API_KEY, imageUrl } from '../constants/constants'
export default {
  name: 'Banner',
  data () {
    return {
      imageUrl,
      maxOverview: 200,
      movie: ''
    }
  },
  mounted () {
    axios.get(`trending/all/week?api_key=${API_KEY}&language=en-US`)
      .then((response) => {
        const movieNum = Math.floor(Math.random() * (response.data.results.length - 1))
        this.movie = response.data.results[movieNum]
      })
  }
}
</script>

<style scoped>
  .banner{
      background-size: cover;
      height: 448px;
      color: rgb(240, 240, 240);
  }
  .content{
      padding-top: 142px;
      height: 190px;
      padding-left: 30px;
  }
  .title{
      font-size: 3rem;
      font-weight: 800;
      padding-bottom: 0.3rem;
  }
  .banner-buttons{
      padding-left: 0;
  }
  .banner-btn{
      color: white;
      outline: none;
      border: none;
      font-weight: 700;
      border-radius: 5px;
      padding-left: 2rem;
      padding-right: 2rem;
      padding-top: 0.5rem;
      padding-bottom: 00.5rem;
      background-color: rgba(51, 51, 51, 0.5);
      cursor: pointer;
      margin-right: 1rem;
  }
  .banner-btn:hover{
      color: black;
      background-color: #e6e6e6; ;
  }
  .description{
      width: 45rem;
      line-height: 1.3;
      padding-top: 1rem;
      font-size: 0.9rem;
      height: 80px;
      max-width: 360px;
  }
  .fade-bottom{
      height: 7.4rem;
      background-image: linear-gradient(180deg, transparent, rgba(37, 37, 37, 0.61), #111);
  }
</style>
