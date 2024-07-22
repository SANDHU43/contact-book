<template>
    <div>
      <h1>Add New Contact</h1>
      <ContactForm @submit="addContact" buttonText="Add" />
    </div>
  </template>
  
  <script>
  import ContactForm from '../components/ContactForm.vue';
  
  export default {
    components: {
      ContactForm,
    },
    methods: {
      addContact(contact) {
        const contacts = JSON.parse(localStorage.getItem('contacts')) || [];
        contact.id = Date.now();
        contacts.push(contact);
        localStorage.setItem('contacts', JSON.stringify(contacts));
        this.$router.push({ name: 'ContactDetail', params: { id: contact.id } });
      },
    },
  };
  </script>
  