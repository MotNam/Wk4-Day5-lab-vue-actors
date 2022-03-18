
<script setup>

import { ref, reactive, computed  } from "vue"

import contacts from "./contacts.json";
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup

const wonOscar = ref(true);
const wonEmmy = ref(true);

const myContacts = reactive (contacts); //Whole list
const listOfFive = reactive (myContacts.slice(0, 5)); //list of 5 actors
const listOfOthers = reactive (myContacts.slice(5)); //list of remaining actors

//1.To choose one random actor: 
function addContact(){
  let chooseOne = Math.floor(Math.random() * listOfOthers.length);

   //console.log(chooseOne);
   console.log(listOfOthers[chooseOne])

   //2.Add the chosen one to initial list of 5
    listOfFive.push (listOfOthers[chooseOne]);

    //3.remove chosen actor from remaining list; (start at, deleteCount)
    listOfOthers.splice (chooseOne, 1);

    console.log(listOfFive);
    console.log(listOfOthers);
}
 
function sortByPopul(){
  listOfFive.sort ((a, b) => (a.popularity < b.popularity ? 1 : -1));
}

function sortByName() {
   listOfFive.sort ((a, b) => (a.name > b.name ? 1 : -1));
}

function removeContact(index) {
  //remove 1 contact starting at 'index' 
    listOfFive.splice(index, 1);
  
}

</script>

<template>

<div class="actors-list">
  <h1>IronContacts</h1>
 
<button @click="addContact">Add New Contact 
</button>

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
 
  <div v-for="(contact, index) in listOfFive" :key ="contact.id">

 <td><img class="pics" :src="contact.pictureUrl" :alt="foto"></td>
  <td> {{ contact.name }}</td>
  <td> {{ contact.popularity.toFixed(2) }}</td>
 
  <td v-if="contact.wonOscar"> Won Oscar 🏆 </td>
  <td v-else > </td>
 
  <td v-if="contact.wonEmmy">Won Emmy </td>
 <td v-else > </td>

<button @click="removeContact(index)">Delete Contact </button>

  </div>

</div>

  <!-- <HelloWorld msg="Hello Vue 3 + Vite" /> -->

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
  width: 20%;
}

</style>
