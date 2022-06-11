<script>
import axios from 'axios'
import MyItems from './MyItems.vue'

export default {
  name: 'ListOfItems',
  components: {
    'my-items': MyItems
  },
  data() {
    return {
      posts: [],
      isMounted: false
    }
  },
  mounted() {
    axios
      .get('https://hacker-news.firebaseio.com/v0/topstories.json')
      .then((response) => {
        this.posts = this.getTenRandom(response.data)
        this.isMounted = true
      })
  },
  methods: {
    getTenRandom: function(arr) {
      const shuffled = [...arr].sort(() => 0.5 - Math.random());
      return shuffled.slice(0, 10);
    }
  }
}
</script>

<template>
  <my-items v-if="isMounted" :post="this.posts" />
  <p v-else>No stories to display right now - Semes like an api error!</p>
</template>

<style scoped>

</style>
