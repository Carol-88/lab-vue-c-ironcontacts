<template>
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
</template>

<script setup>
import {ref} from 'vue';
import contactsData from './contacts.json'

const contacts = ref(contactsData.slice(0,5))
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
