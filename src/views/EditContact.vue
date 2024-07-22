<template>
    <div v-if="contact">
      <h1>Edit Contact</h1>
      <ContactForm :contact="contact" @submit="updateContact" buttonText="Update" />
    </div>
  </template>
  
  <script>
  import ContactForm from '../components/ContactForm.vue';
  
  export default {
    components: {
      ContactForm,
    },
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
      updateContact(updatedContact) {
        const contacts = JSON.parse(localStorage.getItem('contacts')) || [];
        const index = contacts.findIndex(c => c.id === updatedContact.id);
        contacts.splice(index, 1, updatedContact);
        localStorage.setItem('contacts', JSON.stringify(contacts));
        this.$router.push({ name: 'ContactDetail', params: { id: updatedContact.id } });
      },
    },
  };
  </script>
  