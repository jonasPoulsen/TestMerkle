<script setup>
defineProps({
  msg: {
    type: String,
    required: true
  }
})
</script>

<template>
  <div class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h3>
      Here I'm pressenting 10 random hacker news from the "Hacker news api."
    </h3>
    <h2><a target="_blank" href="https://hacker-news.firebaseio.com/v0/topstories.json">Top stories</a></h2>
    <h2><a target="_blank" href="https://github.com/HackerNews/API">API documentation</a></h2>
  </div>
</template>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
