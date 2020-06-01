<template>
  <form
    class="px-8 pt-6 pb-8 mb-4 bg-white rounded shadow-md"
    name="ask-question"
    action="/thanks"
    method="post"
    data-netlify="true"
    data-netlify-honeypot="bot-field"
  >
    <input type="hidden" name="form-name" value="ask-question" />
    <label
      v-for="(panelist, index) in panelists"
      :key="index"
      class="block mb-2 text-sm font-bold text-gray-700"
    >
      <input
        type="radio"
        name="panelist"
        :value="panelist"
        :checked="panelist === currentPanelist"
        @input="(ev) => updatePanelist"
      />
      <span>{{ panelist }}</span>
    </label>
    <button>Submit</button>
  </form>
</template>
<script>
export default {
  name: 'QAForm',
  data() {
    return {
      panelists: ['Evan You', 'Chris Fritz'],
      currentPanelist: 'Evan You'
    }
  },
  methods: {
    updatePanelist(ev) {
      this.currentPanelist = ev.target.value
    }
  }
}
</script>
