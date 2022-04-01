<template>
  <h1>Data from API</h1>
  <button class="btn">Waiting</button>
  <p>{{ data }}</p>
  <div>
    <ul v-if="messages && messages.length">
      <li v-for="message of messages" :key="message.id">
        {{ message.body }}
      </li>
    </ul>
    <ul v-if="errors && errors.length">
      <li v-for="error of errors" :key="error.id">
        {{ error.message }}
      </li>
    </ul>
  </div>
</template>

<script>
const API_URL = "https://homeassignment.FOO.com/";
const config = {
  method: "POST",
  headers: {
    "Content-Type": "text/plain",
    "Access-Control-Allow-Origin": "*",
  },
  body: {
    "lang": "eng",
    "company_account_id": "FOO",
    "apiKey": "BAR",
  },
};

export default {
  name: "api-component",
  data() {
    return {
      data: null,
      messages: [],
      errors: [],
    };
  },
  async created() {
    try {
      const response = await fetch(API_URL, config).then(
        (response) => (this.messages = response)
      );
      console.log(response);
    } catch (e) {
      this.errors.push(e);
      console.log(e, "Hey, I am inside the errors");
    }
  },
};
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: rgb(0, 179, 179);
}
.btn {
  border: 2px solid rgb(0, 179, 179);
  background-color: #fff;
  width: 80px;
  font-size: 1em;
  border-radius: 5px;
}
.btn:hover {
  background: rgb(0, 179, 179);
  color: #fff;
}
</style>