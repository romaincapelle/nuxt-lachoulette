<template>
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
      <div>
        <label class="block mb-2 text-sm font-bold text-gray-700" for="name"
          >Name:</label
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
          class="h-full py-0 pl-2 text-gray-500 bg-transparent border-transparent form-select pr-7 sm:text-sm sm:leading-5"
        >
          <option>USD</option>
          <option>CAD</option>
          <option>EUR</option>
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
export default {}
</script>

<style></style>
