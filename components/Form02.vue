<template>
  <div class="w-full max-w-xs">
    <form
      class="px-8 pt-6 pb-8 mb-4 bg-white rounded shadow-md"
      name="contactus"
      action="/thanks"
      method="post"
      netlify
      netlify-honeypot="bot-field"
      @submit.prevent="handleSubmit"
    >
      <input type="hidden" name="form-name" value="contactus" />
      <div>
        <label class="block mb-2 text-sm font-bold text-gray-700" for="name"
          >Votre nom :</label
        >
        <input
          class="w-full px-3 py-2 leading-tight text-gray-700 border rounded shadow appearance-none focus:outline-none focus:shadow-outline"
          type="text"
          name="name"
          required
        />
      </div>
      <div>
        <label class="block mb-2 text-sm font-bold text-gray-700" for="email"
          >Email:</label
        >
        <input
          class="w-full px-3 py-2 leading-tight text-gray-700 border rounded shadow appearance-none focus:outline-none focus:shadow-outline"
          type="email"
          name="email"
          required
        />
      </div>
      <div>
        <label for="message">Message:</label>
        <textarea
          class="w-full px-3 py-2 leading-tight text-gray-700 border rounded shadow appearance-none focus:outline-none focus:shadow-outline"
          name="message"
          required
        ></textarea>
      </div>
      <div>
        <select
          aria-label="Currency"
          name="currency"
          class="w-full h-8 py-0 text-gray-500 bg-transparent border pr-7 sm:text-sm sm:leading-5"
          ><option value="" disabled="" selected=""
            >Choose Flooring type</option
          >
          <option value="usd" name="usd">USD</option>
          <option value="cad" name="cad">CAD</option>
          <option value="eur" name="eur">EUR</option>
        </select>
      </div>
      <button
        class="px-4 py-2 font-bold text-white bg-blue-500 rounded hover:bg-blue-700 focus:outline-none focus:shadow-outline"
        type="submit"
        value="Send message"
      >
        Send
      </button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      biere: {
        nomDeLaBiere: '',
        nombreDeBiere: 0
      },
      selectedOption: 'C',
      bieres: [
        { text: 'Biere Blonde' },
        { text: 'Biere Brune' },
        { text: 'Biere Ambrée' }
      ]
    }
  },
  methods: {
    encode(data) {
      return Object.keys(data)
        .map(
          (key) => encodeURIComponent(key) + '=' + encodeURIComponent(data[key])
        )
        .join('&')
    },
    handleSubmit(e) {
      fetch('/', {
        method: 'POST',
        headers: { 'Content-Type': 'application/x-www-form-urlencoded' },
        body: this.encode({
          'form-name': e.target.getAttribute('name'),
          ...this.formData
        })
      })
        .then(() => this.$router.push('/thanks'))
        .catch((error) => alert(error))
    }
  }
}
</script>

<style></style>
