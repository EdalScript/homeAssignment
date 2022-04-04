<template>
  <h1>Data from API</h1>
  <button class="btn">Waiting</button>
  <p>{{ statuses }}</p>
</template>

<script>
import axios from "axios";
const company_account_id = "FOO";
const apiKey = "BAR";
const config = {
  method: "POST",
  body: {
    "lang": "eng",
  },
};

export default {
  name: "api-component",
  data() {
    return {
      data: null,
      statuses: [],
    };
  },
  async created() {
    try {
      const response = await axios
        .post("/api/v2/statuses/list", {company_account_id, apiKey, config})
        .then((response) => (this.statuses = response.data));
      console.log(response.data);
    } catch (e) {
      this.errors.push(e);
      console.log(e);
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
  color: #47c1bf;
}
.btn {
  border: 2px solid #47c1bf;
  background-color: #fff;
  width: 80px;
  font-size: 1em;
  border-radius: 5px;
}
.btn:hover {
  background: #47c1bf;
  color: #fff;
}
</style>