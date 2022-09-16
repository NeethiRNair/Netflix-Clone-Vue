<template>
  <div class="home">
    <banner />
    <row-post :url="originals" title="Netflix Originals" />
    <row-post :url="action" title="Action" isSmall="isSmall"/>
    <row-post :url="trending" title="Trending" isSmall="isSmall"/>
    <row-post :url="comedy" title="Comedy" isSmall="isSmall"/>
    <row-post :url="horror" title="Horror" isSmall="isSmall"/>
    <row-post :url="romance" title="Romance" isSmall="isSmall"/>
    <row-post :url="documentaries" title="Documentaries" isSmall="isSmall"/>
  </div>
</template>

<script>
import Banner from './Banner.vue'
import RowPost from './RowPost.vue'
import { originals, action, trending, comedy, horror, romance, documentaries } from '../constants/urls'

export default {
  components: { Banner, RowPost },
  name: 'Home',
  data () {
    return {
      originals,
      action,
      trending,
      comedy,
      horror,
      romance,
      documentaries
    }
  }
}
</script>

<style scoped>

</style>
