<template>
 <section>
    <button @click="addRandomContact">Add random Contact</button>
    <button @click="sortByPopularity">Sort by popularity</button>
    <button @click="sortByName">Sort by name</button>
    <table>
      <thead>
        <tr>
          <th>Picture</th>
          <th>Name</th>
          <th>Popularity</th>
          <th>Won an Oscar</th>
          <th>Won an Emmy</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="contact in contacts" :key="contact.id">
          <td><img :src="contact.pictureUrl" alt="Contact Picture" width="50"></td>
          <td>{{ contact.name }}</td>
          <td>{{ contact.popularity }}</td>
          <td>
            <span v-if="contact.wonOscar">🏆</span>
          </td>
          <td>
            <span v-if="contact.wonEmmy">🏆</span>
          </td>
        </tr>
      </tbody>
    </table>
 </section>
</template>

<script setup>
import { ref } from 'vue';
import contactsData from './contacts.json';

const contacts = ref(contactsData.slice(0, 5));
const randomContacts = ref(contactsData.slice(5));

const addRandomContact = () => {
  if (randomContacts.value.length > 0) {
    const randomContact = randomContacts.value.splice(Math.floor(Math.random() * randomContacts.value.length), 1)[0];
    contacts.value.push(randomContact);
 }
};

const sortByPopularity = () => {
  contacts.value.sort((a, b) => b.popularity - a.popularity);
};

const sortByName = () => {
  contacts.value.sort((a, b) => a.name.localeCompare(b.name));
};
</script>

<style>
table {
 width: 100%;
 border-collapse: collapse;
}

th, td {
 border: 1px solid #ddd;
 padding: 8px;
}

th {
 background-color: #f2f2f2;
}
</style>
