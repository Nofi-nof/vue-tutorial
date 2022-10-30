<template>
  <div>
    <h1>Hello World</h1>
    <ul>
      <li v-for="article in articles" :key="article.id">
        {{ article.title }}
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    data: () => ({
      articles: [],
    }),
    async created() {
      const res = await fetch(
        'https://qiita.com/api/v2/items?page=1&per_page=20'
      )
      this.articles = await res.json()
    },
  }
</script>
