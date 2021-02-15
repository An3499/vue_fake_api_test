<template>
  <div id="app">
    <User
    v-for="user in users"
    :key="user.id"
    :user='user'/>
  </div>
</template>

<script lang="ts">
import Vue from "vue";
import User from './components/User.vue';
import { IUser } from "@/types";

export default Vue.extend({
  name: "App",
  components:{
    User
  },
  data() {
    return {
      users: Array,
    };
  },

  methods: {
    async getUsers() {
      let response = await fetch("https://jsonplaceholder.typicode.com/users");
      let usersFromServer = await response.json();
      this.users = usersFromServer;
    },
  },

  beforeMount(){
    this.getUsers()
  }
});
</script>

<style scoped lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
