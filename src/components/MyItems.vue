<script>
import axios from 'axios'
import TheItem from './TheItem.vue'
export default {
  name: 'MyItems',
  components: {
    'the-item': TheItem
  },
  props: ['post'],
  created() {
    this.post.forEach((postId) => {
      this.getPostData(postId)
    });
  },
  data() {
    return {
      postdata: []
    }
  },
  methods: {
    getPostData: function(postId) {
      axios
        .get('https://hacker-news.firebaseio.com/v0/item/' + postId + '.json')
        .then((response) => {

          this.postdata.push(  response.data )

        })
    }
  },
  computed: {
    sortThePosts: function() {

      return this.postdata.sort((a, b) => a.score - b.score)
    }
  }
}
</script>

<template>

  <div class="">

    <h1>Hacker News List</h1>

    <the-item v-for="pd in this.sortThePosts" :postdata="pd" :key="pd.by" />


  </div>

</template>

<style scoped>
  h1 {
    font-weight: bold;
    padding-top: 15px;
    padding-bottom: 20px;
  }
</style>
