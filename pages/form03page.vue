<template>
  <form
    name="contact"
    method="post"
    action="/success"
    netlify
    data-netlify-honeypot="bot-field"
  >
    <input type="hidden" name="form-name" value="contact" />
    <div>
      <label for="name" class="label">Votre nom :</label>
      <input type="text" name="name" />
    </div>
    <div>
      <label for="email" class="label">Votre email :</label>
      <input type="text" name="email" />
    </div>
    <div>
      <label for="email" class="label">Votre email :</label>
      <select v-model="selectedOption">
        <option
          v-for="option in beerOptions"
          :key="option.value"
          :value="option.value"
        >
          {{ option.label }}
        </option>
      </select>
      <button type="button" @click="addBeer">Add Beer</button>
    </div>
    <ul class="beer-list">
      <li v-for="item in selectedBeers" :key="item.value">
        🍺 {{ item.label }} x {{ item.quantity }}
        <input hidden :name="item.value" :value="item.quantity" />
      </li>
    </ul>
    <button type="submit">Send</button>
  </form>
</template>

<script>
export default {
  name: 'Form',
  data() {
    return {
      selectedBeers: [],
      beerOptions: [
        { label: 'Biére Brune', value: 'brune', quantity: 0 },
        { label: 'Biére Blonde', value: 'blonde', quantity: 0 },
        { label: 'Biére Ambreé', value: 'ambree', quantity: 0 }
      ],
      selectedOption: 'brune'
    }
  },
  computed: {},
  methods: {
    addBeer() {
      const selectedBeer = this.beerOptions.find((item) => {
        return item.value == this.selectedOption
      })
      selectedBeer.quantity++
      const existingBeer = this.selectedBeers.find((beer) => {
        return beer.value === selectedBeer.value
      })
      if (existingBeer) {
        selectedBeer.quantity = existingBeer.quantity
      } else {
        this.selectedBeers.push(selectedBeer)
      }
    },
    deleteBeer() {}
  }
}
</script>
<style scoped></style>
