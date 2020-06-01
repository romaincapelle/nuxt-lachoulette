<template>
  <div>
    <form
      name="contactus"
      action="/thanks"
      method="post"
      netlify
      netlify-honeypot="bot-field"
    >
      <input type="hidden" name="form-name" value="contactus" />
      <div>
        <label for="name">Name:</label>
        <input class="border" type="text" name="name" required />
      </div>
      <div>
        <input class="border" type="email" name="email" required />
        <label for="email">Email:</label>
      </div>
      <div>
        <textarea class="border" name="message" required></textarea>
        <label for="message">Message:</label>
      </div>
      <button class="border" type="submit" value="Send message">Send</button>
    </form>
  </div>
</template>

<script>
export default {}
</script>

<style></style>
