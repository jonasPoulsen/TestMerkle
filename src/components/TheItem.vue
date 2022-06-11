<script>
import axios from 'axios'
export default {
  name: 'TheItem',
  props: ['postdata'],
  mounted() {

    axios
    .get('https://hacker-news.firebaseio.com/v0/user/' + this.postdata.by + '.json')
    .then((response) => {
      this.kForThis = response.data.karma
    })

  },
  data() {
    return {
      kForThis: 0
    }
  }
}
</script>

<template>

  <div class="storyItem">
    <h2>Score - {{ this.postdata.score }}</h2>
    <h3>{{ this.postdata.title }}</h3>
    <h4>By: {{ this.postdata.by }} - Karma: {{ this.kForThis }}</h4>
    <a v-if="this.postdata.url" target="_blank" :href="this.postdata.url">Link to the story</a>
    <h5 v-else>Sorry - No link was found!</h5>
    <p>Time: {{ this.postdata.time }}</p>

    <img alt="news icon" src="@/assets/news-icon-vector-13.jpg" width="40" height="30" />
  </div>

</template>

<style lang="scss" scoped>
  .storyItem {
    background-color: #D4E6F1;
    border-left: 4px solid #7FB3D5;
    margin-bottom: 10px;
    padding-bottom: 10px;
    * {
      padding-left: 10px;
    }
    h2 {
      background-color: #7FB3D5;
      color: white;
      padding: 10px;
    }
    h3 {
      padding-top: 10px;
    }
    p {
      font-size: 12px;
      margin-bottom: 10px;
    }
  }
</style>
