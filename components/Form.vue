<template>
  <div>
    <h1>1</h1>
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
    <h2>2</h2>
    <div class="w-full max-w-xs">
      <form
        class="px-8 pt-6 pb-8 mb-4 bg-white rounded shadow-md"
        name="contactus"
        action="/thanks"
        method="post"
        netlify
        netlify-honeypot="bot-field"
      >
        <input type="hidden" name="form-name" value="contactus" />
        <div class="mb-4">
          <label
            class="block mb-2 text-sm font-bold text-gray-700"
            for="username"
          >
            Username
          </label>
          <input
            id="username"
            class="w-full px-3 py-2 leading-tight text-gray-700 border rounded shadow appearance-none focus:outline-none focus:shadow-outline"
            type="text"
            placeholder="Username"
          />
        </div>
        <div class="mb-6">
          <label
            class="block mb-2 text-sm font-bold text-gray-700"
            for="password"
          >
            Password
          </label>
          <input
            id="password"
            class="w-full px-3 py-2 mb-3 leading-tight text-gray-700 border border-red-500 rounded shadow appearance-none focus:outline-none focus:shadow-outline"
            type="password"
            placeholder="******************"
          />
          <p class="text-xs italic text-red-500">Please choose a password.</p>
        </div>
        <div class="flex items-center justify-between">
          <button
            class="px-4 py-2 font-bold text-white bg-blue-500 rounded hover:bg-blue-700 focus:outline-none focus:shadow-outline"
            type="button"
          >
            Sign In
          </button>
          <a
            class="inline-block text-sm font-bold text-blue-500 align-baseline hover:text-blue-800"
            href="#"
          >
            Forgot Password?
          </a>
        </div>
      </form>
      <p class="text-xs text-center text-gray-500">
        &copy;2020 Acme Corp. All rights reserved.
      </p>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style></style>
