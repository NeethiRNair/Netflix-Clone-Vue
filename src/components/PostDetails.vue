<template>
  <div class="postdetails">
    <div class="video-container">
      <youtube :video-id="movieUrlId" :player-vars="opts.playerVars" :width="opts.width" :height="opts.height" />
    </div>
    <div class='content'>
      <h1 class='title'>{{ movie.title? movie.title : movie.name }}</h1>
      <div class='banner-buttons'>
          <button class='banner-btn'>Play</button>
          <button class='banner-btn'>My List</button>
          <button class='banner-btn'>Download</button>
      </div>
      <h3 class='description'>{{movie ? movie.overview : ''}}</h3>
    </div>
  </div>
</template>

<script>
import { API_KEY } from '../constants/constants'
import axios from '../axios'

export default {
  components: { },
  name: 'PostDetails',
  data () {
    return {
      movie: {},
      movieId: this.$route.params.id,
      movieUrlId: '',
      opts: {
        height: '400',
        width: '80%',
        playerVars: {
          autoplay: 1
        }
      }
    }
  },
  mounted () {
    axios.get(`movie/${this.movieId}/videos?api_key=${API_KEY}&language=en-US`)
      .then((response) => {
        if (response.data.results.length !== 0) {
          this.movieUrlId = response.data.results[0].key
        }
      })
    axios.get(`movie/${this.movieId}?api_key=${API_KEY}&language=en-US`)
      .then((response) => {
        this.movie = response.data
      })
  }
}
</script>

<style scoped>
  .video-container {
    text-align: center;
  }
  .content{
      height: 190px;
      padding-top: 10px;
      padding-left: 30px;
      color: white;
      text-align: center;
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
      padding: 0 150px;
      line-height: 1.3;
      padding-top: 1rem;
      font-size: 0.9rem;
      height: 80px;
  }
</style>
