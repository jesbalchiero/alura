<template>
  <div id="app">
    <h2>{{ titleWebPage }}</h2>
    <ul>
      <li v-for="p in photos">
        <img :src="p.url" :alt="p.titulo" />
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'app',
  data () {
    return {
      titleWebPage: 'Curso Vue Alura',
      photos: [],
    }
  },
  created() {
    this.$http.get("http://localhost:3000/v1/fotos")
      .then(res => res.json())
      .then(p => this.photos = p, err => console.log(err));
  }
}
</script>

<style>

</style>
