<script setup>

import { ref, reactive  } from "vue"

import contacts from "./contacts.json";
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup

let myContacts = contacts;
let listOfFive = myContacts.splice(5);
// console.log(myContacts);

const wonOscar = ref(true);
const wonEmmy = ref(true);

function addRandom(){
  let randomContacts = this.myContacts.length - this.listOfFive.length;

  let chooseOne = (Math.random()*randomContacts.length) * randomContacts.length;
  
  console.log(chooseOne.value)
    
};
 
let  newList = listOfFive += chooseOne;

// evenNumbers: function () {
//     return this.numbers.filter(function (number) {
//       return number % 2 === 0
//     })
//   }

// evenNumbers: function () {
//     return this.numbers.sort(function (number) {
//       return number % 2 === 0
//     })
//   }

</script>

<template>



<div class="actors-list">
  <caption>IronContacts</caption>
 
  <button @click="addRandom">Add New Contact 
</button>
{{newList.value}}

<button @click="sortByPopul">Sort by Popularity 
</button>

<button @click="sortByName">Sort by Name
</button>


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

<td>{{chooseOne.contact.name}}</td>
<td>{{chooseOne.contact.popularity}}</td>

  </div>

  

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
