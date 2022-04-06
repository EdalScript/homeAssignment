<template>
  <h1>Data from API</h1>

  <main>
    <div class="list-container">
      <button class="btn">Waiting</button>
      <div class="dropdown">
        <ul>
          <li v-for="(status, index) in statuses.data" :key="index">
            <span

              class="status-color"
              :style="{ 'background-color': status.color }"
            ></span>
            {{ status.status_name }}
          </li>
        </ul>
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";
const company_account_id = "FOO";
const apiKey = "BAR";
const config = {
  method: "POST",
  body: {
    lang: "eng",
  },
};

export default {
  name: "api-component",
  data() {
    return {
      statuses: [],
    };
  },
  async created() {
    try {
      const response = await axios
        .post("/api/v2/statuses/list", { company_account_id, apiKey, config })
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
main {
  display: flex;
  align-items: center;
  justify-content: center;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
  position: relative;
  padding: 0;
  box-shadow: 0px 0px 30px 15px rgba(97, 93, 93, 0.055);
  width: 250px;
  cursor: pointer;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}
li {
  display: inline-block;
  padding: 0.7em;
  list-style: none;
  vertical-align: middle;
  width: 90%;
}

li:hover {
  background-color: rgba(154, 194, 201, 0.055);
}

li:active {
  background-color: rgba(96, 201, 219, 0.11);
  border-left: 3px solid rgb(20, 147, 197);
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
.status-color {
  height: 15px;
  width: 15px;
  border-radius: 50%;
  display: inline-block;
  border: 4px solid white;
  vertical-align: middle;
}
</style>