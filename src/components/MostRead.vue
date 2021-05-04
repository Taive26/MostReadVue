<template>
 <input v-model="day" placeholder="Päev" />
 <input v-model="month" placeholder="Kuu" />
 <input v-model="year" placeholder="Aasta" />
<div id="button">
  <button v-on:click="getMostReadArticles">OTSI</button>
</div>

<div v-for="(article, index) in articles">
{{ index+1 }}
{{ article.titlesnormalized }} 
{{ article.description }}
<a :href="article.content_urls.desktop.page">
<div v-if="article.thumbnail" class="entry-thumbnail">
<img :src="article.thumbnail.source" />
</a>
</div>
</div>


</template>

<script>
import axios from "axios";
export default {
  name: "MostRead",
  props: {
    msg: String
  },
    data() {
    return {
      day: "",
      month: "",
      year: "",
      articles: null,
      loading: true,
      errored: false
    }
  },
 
  methods: {
    getMostReadArticles() {
axios
      .get(`https://en.wikipedia.org/api/rest_v1/feed/featured/${this.year}/${this.month}/${this.day}`)
      .then(response => {
        console.log(response.data.mostread.articles)
        this.articles = response.data.mostread.articles
      })
      .catch(error => {
        console.log(error)
        this.errored = true
      })
      .finally(() => this.loading = false)
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
