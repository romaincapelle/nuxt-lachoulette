<template>
  <form ... @submit.prevent="handleSubmit">
    <label v-for="(panelist, index) in panelists" :key="index">
      <input
        type="radio"
        name="panelist"
        :value="panelist"
        :checked="form.askPerson === panelist"
        @input="(ev) => (form.askPerson = ev.target.value)"
      />
      <span>{{ panelist }}</span>
      <button>Submit</button>
    </label>
  </form>
</template>
<script>
import axios from 'axios'

export default {
  name: 'Form',
  data() {
    return {
      panelists: ['Evan You', 'Chris Fritz'],
      currentPanelist: 'Evan You',
      form: {
        askPerson: ''
      }
    }
  },
  methods: {
    encode(data) {
      return Object.keys(data)
        .map(
          (key) => `${encodeURIComponent(key)}=${encodeURIComponent(data[key])}`
        )
        .join('&')
    },
    handleSubmit() {
      const axiosConfig = {
        header: { 'Content-Type': 'application/x-www-form-urlencoded' }
      }
      axios.post(
        '/',
        this.encode({
          'form-name': 'ask-question',
          ...this.form
        }),
        axiosConfig
      )
    }
  }
}
</script>
