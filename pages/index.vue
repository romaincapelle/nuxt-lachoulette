<template>
  <Layout>
    <form
      name="contact"
      method="post"
      action="/success/"
      data-netlify="true"
      data-netlify-honeypot="bot-field"
      netlify
      netlify-honeypot="bot-field"
      @submit.prevent="handleSubmit"
    >
      <input type="hidden" name="form-name" value="contact" />
      <p hidden>
        <label> Don’t fill this out: <input name="bot-field" /> </label>
      </p>
      <div class="sender-info">
        <div>
          <label for="name" class="label">Votre nom :</label>
          <input v-model="formData.name" type="text" name="name" required />
        </div>
        <div>
          <label for="email">Votre email :</label>
          <input v-model="formData.email" type="email" name="email" required />
        </div>
        <div>
          <label for="phone">Votre numéro de téléphone :</label>
          <input
            v-model="formData.phone"
            placeholder="ex: 0327357244"
            type="text"
            name="phone"
            required
          />
        </div>
        <div>
          <label for="enlevement">Le jour d’enlèvement :</label>
          <input
            v-model="formData.enlevement"
            type="date"
            name="enlevement"
            required
          />
        </div>
      </div>

      <div class="message-wrapper">
        <label for="message">Message</label>
        <textarea v-model="formData.message" name="message" required></textarea>
      </div>

      <div>
        <label for="naissance">Date de naissance :</label>
        <input
          v-model="formData.naissance"
          type="date"
          max="0"
          name="naissance"
          required
        />
      </div>

      <order :updatedbeers.sync="updatedbeers" />
      <button type="submit">Commander</button>
    </form>
    <p>formData</p>
    <p>{{ formData }}</p>
    <p>updatedbeers</p>
    <p>{{ updatedbeers }}</p>
    <p>completeFormData</p>
    <p>{{ completeFormData }}</p>
  </Layout>
</template>

<script>
import Order from '../components/Order'
export default {
  metaInfo: {
    title: 'Hello, world!'
  },
  components: {
    Order
  },
  data() {
    return {
      formData: {},
      updatedbeers: []
    }
  },
  computed: {
    completeFormData() {
      const formData = this.formData
      const updatedbeers = this.updatedbeers
      const obj = {}
      updatedbeers.forEach((item) => {
        obj[item.nomDeLaBiere] = item.nombreDeBiere
      })
      const completeData = { ...formData, ...obj }
      return completeData
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

<style>
.home-links a {
  margin-right: 1rem;
}
</style>
