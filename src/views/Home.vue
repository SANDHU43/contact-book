<template>
    <div>
      <h1>Contact Book</h1>
      <ContactList />
      <router-link to="/add" class="btn">Add New Contact</router-link>
    </div>
  </template>
  
  <script>
  import ContactList from '../components/ContactList.vue';
  
  export default {
    components: {
      ContactList,
    },
  };
  </script>
  
  <style scoped>
  h1 {
    font-size: 2.5em;
    margin-bottom: 20px;
  }
  
  .btn {
    display: inline-block;
    padding: 10px 20px;
    margin: 10px 0;
    color: white;
    background-color: #42b983;
    text-decoration: none;
    text-align: center;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .btn:hover {
    background-color: #369b71;
  }
  
  ul {
    list-style-type: circle;
    padding-left: 20px;
  }
  
  li {
    margin: 10px 0;
  }
  </style>
  