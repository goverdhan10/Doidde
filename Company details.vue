<template>
  <b-container class="main">
    <!-- <h4 class="text-center">List page</h4> -->
    <div v-if="!userdata">
      <b-table striped hover :items="results" :fields="fields" @row-clicked="clickHandler"></b-table>
    </div>
   <div v-if="userdata">
         <b-jumbotron class="data">
            <h2 class="text-center">Employee Information</h2>
        <b-button @click="back">back</b-button>
        <p>Id:{{currentuser.id}}</p>
        <p>Name:{{currentuser.name}}</p>
        <p>Username:{{currentuser.username}}</p>
        <p>Email:{{currentuser.email}}</p>
        <p>Address:{{currentuser.address.street}}, {{currentuser.address.suite}}, {{currentuser.address.city}}, {{currentuser.address.zipcode}}</p>
        <p>Phone:{{currentuser.phone}}</p>
        <p>Website:{{currentuser.website}}</p>
        <p>Company:{{currentuser.company.name}}, {{currentuser.company.catchPhrase}}, {{currentuser.company.bs}}</p>
           </b-jumbotron>
      </div>
  </b-container>
  </template>
<script>
import axios from "axios";
export default {
  data() {
    return {
      fields: ["name", "username", "email"],
      results: [],
      userdata: false,
      currentuser: {}
    };
  },
  methods: {
    clickHandler(items) {
      this.userdata = true;
      this.currentuser = items;
    },
    back() {
      this.userdata = false;
    }
  },
  mounted() {
    axios.get("https://jsonplaceholder.typicode.com/users").then(response => {
      this.results = response.data;
    });
  }
};
</script>
<style  scoped>
.data {
  text-align: center;
  background-color: aqua;
  font-size:20px;
}
button {
float: right;
}
.main{
  padding:40px;
}
</style>
