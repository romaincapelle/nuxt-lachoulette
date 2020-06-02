<template>
  <div id="main">
    <BeerForm @submit="addBeer" />

    <h3>beer</h3>
    <ul></ul>
  </div>
</template>

<script>
import BeerForm from './BeerForm.vue'
export default {
  name: 'BeerList',
  components: {
    BeerForm
  },
  data() {
    return {
      beers: [],
      completed: []
    }
  },
  methods: {
    addBeer(beer) {
      this.beers.push(beer)
      this.$emit('update:updatedbeers', this.beers)
    }
  }
}
</script>

<style scoped>
h1 {
  text-align: center;
  margin: 40px 0;
}
ul {
  margin: 0;
  padding: 0;
}
</style>
