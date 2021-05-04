<template>
 <input v-model="day" placeholder="Päev" />
 <input v-model="month" placeholder="Kuu" />
 <input v-model="year" placeholder="Aasta" />

<!---
<span v-for="(article, index) in articles">
    {{ index }} {{ article }}
</span> -->

<div id="app">
  {{ articles }}
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
      day: null,
      month: null,
      year: null,
      articles: null,
      loading: true,
      errored: false
    }
  },
  mounted() {
    axios
      .get('https://en.wikipedia.org/api/rest_v1/feed/featured/2021/04/30')
      .then(response => {
        console.log(response)
        this.articles = response
      })
      .catch(error => {
        console.log(error)
        this.errored = true
      })
      .finally(() => this.loading = false)
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
