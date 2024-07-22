<template>
    <div v-if="contact" class="container">
      <h1>{{ contact.firstName }} {{ contact.lastName }}</h1>
      <p>Email: {{ contact.email }}</p>
      <router-link :to="{ name: 'EditContact', params: { id: contact.id } }" class="btn btn-edit">Edit</router-link>
      <button @click="deleteContact" class="btn btn-delete">Delete</button>
      <router-link to="/" class="btn btn-back">Back to Contact Book</router-link>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        contact: null,
      };
    },
    created() {
      const contacts = JSON.parse(localStorage.getItem('contacts')) || [];
      this.contact = contacts.find(c => c.id === parseInt(this.$route.params.id));
    },
    methods: {
      deleteContact() {
        const contacts = JSON.parse(localStorage.getItem('contacts')) || [];
        const updatedContacts = contacts.filter(c => c.id !== parseInt(this.$route.params.id));
        localStorage.setItem('contacts', JSON.stringify(updatedContacts));
        this.$router.push('/');
      },
    },
  };
  </script>
  
  <style scoped>
  .container {
    max-width: 600px;
    margin: 0 auto;
    padding: 20px;
    text-align: center;
  }
  
  h1 {
    font-size: 2em;
    margin-bottom: 0.5em;
  }
  
  p {
    font-size: 1.2em;
    margin-bottom: 1em;
  }
  
  .btn {
    display: inline-block;
    padding: 10px 20px;
    margin: 5px;
    color: white;
    text-decoration: none;
    text-align: center;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .btn-edit {
    background-color: #4CAF50;
  }
  
  .btn-delete {
    background-color: #f44336;
  }
  
  .btn-back {
    background-color: #2196F3;
  }
  
  .btn:hover {
    opacity: 0.8;
  }
  </style>
  