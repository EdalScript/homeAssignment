<template>
  <h1>Data from API</h1>
  <button class="btn">Waiting</button>
  <div>
     <ul v-if="statuses && statuses.length">
      <li v-for="[status_id, status_name] in statuses" :key="status_id">
        {{ status_id }} is {{ status_name}}
      </li>
    </ul>
  </div>
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
  //Hi Joosep! Thanks for the tip, it did help a lot! 
  //I'm having a lot of fun working in this homework and funnily enough it's just a homework-- yet quite challenging.
  //I spent too much time understanding the API, how embarrassing! But I learned a lot thanks to this experience. 
  //I'm quite stubborn myself to let this homework unfinished so I will continue working on this even if it's late
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