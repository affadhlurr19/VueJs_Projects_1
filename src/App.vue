<template>
  <div id="app">
    <h1>Klik Disini Untuk Memulai Ujian</h1><br>
    <router-link to= "/soal">Mulai</router-link>
    <router-link to= "/">Selesai</router-link>
    <router-view/>
  </div>
</template>
<script>
export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
