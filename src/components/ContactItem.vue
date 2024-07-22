<template>
    <li v-if="contact && contact.firstName && contact.lastName">
      <router-link :to="{ name: 'ContactDetail', params: { id: contact.id } }" class="contact-link">
        {{ contact.firstName }} {{ contact.lastName }}
      </router-link>
    </li>
  </template>
  
  <script>
  export default {
    props: {
      contact: {
        type: Object,
        required: true,
      },
    },
  };
  </script>
  
  <style scoped>
  .contact-link {
    color: #42b983;
    text-decoration: none;
  }
  
  .contact-link:hover {
    text-decoration: underline;
  }
  </style>
  