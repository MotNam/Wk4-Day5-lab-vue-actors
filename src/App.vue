<script setup>
import { ref } from "vue"

import contacts from "./contacts.json";
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import HelloWorld from "./components/HelloWorld.vue";

const myContacts = contacts;
// myContacts.splice(15);
// console.log(myContacts);

const wonOscar = ref(true);
const wonEmmy = ref(true);

 
</script>

<template>
<div class="actors-list">
  <caption>IronContacts</caption>
  <td>
    <th>Picture</th>

    <th>Name</th>

    <th>Popularity</th>

    <th>Won an Oscar</th>

    <th>Won an Emmy</th>


  </td>
 
  <div v-for="contact in myContacts" :key="contact.id">

 <td><img class="pics" :src="contact.pictureUrl" alt="foto"></td>
  <td> {{ contact.name }}</td>
  <td> {{ contact.popularity.toFixed(2) }}</td>
  <td v-if="contact.wonOscar"> Won Oscar 🏆 </td>
  <td v-else > </td>
  <td v-if="contact.wonEmmy">Won Emmy </td>
 <td v-else > </td>

<button @click="addRandom"></button>
  </div>

  <img alt="Vue logo" src="./assets/logo.png" />

</div>

  <HelloWorld msg="Hello Vue 3 + Vite" />

</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.actors-list{
  display:flex; 
  flex-direction: column;
 } 
.pics {
  width: 30%;
}



</style>
