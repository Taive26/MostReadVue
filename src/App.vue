<template>
  <div id="app">
    <img alt="Vue logo" src="https://gelinasjames.com/wp-content/uploads/2019/03/curious-team.png" width=200>
    <h1>Popimad Wikipedia artiklid</h1>
    <MostRead/>
  </div>
</template>

<script>
import axios from `axios`
import MostRead from './components/MostRead.vue'

export default {
  name: 'App',
  components: {
    MostRead
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
