<template>
  <h1>Scoro</h1>

  <main>
    <div class="list-container">
      <button @click="toggle" class="btn">Waiting</button>
      <div v-if="active" @mouseleave="handleEvent" class="dropdown">
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
const company_account_id = "apiplayground";
const apiKey = "ScoroAPI_ee8e5c35acefcbe";
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
      active: false,
    };
  },
  methods: {
    toggle() {
      this.active = !this.active;
    },
    handleEvent() {
      this.active = !this.active;
    },
  },
  async created() {
    try {
      const response = await axios
        .post("/api/v2/statuses/list", { company_account_id, apiKey, config })
        .then((response) => (this.statuses = response.data));
      console.log(response.data);
    } catch (e) {
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
  top: -9px;
  box-shadow: 0px 0px 15px 5px rgba(97, 93, 93, 0.075);
  cursor: pointer;
  display: flex;
  flex-direction: column;
  justify-content: space-around;
}
li {
  display: inline-block;
  padding: 0.9em;
  list-style: none;
  text-align: left;
  max-width: 160px;
  margin-left: 3px;
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
/* Style for button and status color*/
.list-container {
  font-size: 0.75em;
  font-weight: 400;
  border-radius: 4px;
}
.dropdown {
  overflow-y: scroll;
  max-height: 250px;
}
::-webkit-scrollbar {
  width: 7px;
}
::-webkit-scrollbar-track {
  box-shadow: inset 0 0 5px grey;
  border-radius: 10px;
}
::-webkit-scrollbar-thumb {
  background: #47c1bf;
  border-radius: 10px;
}
.btn {
  border: 2px solid #47c1bf;
  background-color: #fff;
  width: 80px;
  font-size: 1em;
  border-radius: 5px;
  cursor: pointer;
}
.btn:hover {
  background: #47c1bf;
  color: #fff;
}
.status-color {
  height: 12px;
  width: 12px;
  border-radius: 50%;
  display: inline-block;
  border: 4px solid white;
  vertical-align: middle;
}
</style>