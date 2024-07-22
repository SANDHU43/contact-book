<template>
  <div>
    <input v-model="search" placeholder="Search by name" class="search-bar" />
    <ul class="contact-list">
      <ContactItem
        v-for="contact in filteredContacts"
        :key="contact.id"
        :contact="contact"
      />
    </ul>
  </div>
</template>

<script>
import ContactItem from './ContactItem.vue';

export default {
  components: {
    ContactItem,
  },
  data() {
    return {
      search: '',
      contacts: JSON.parse(localStorage.getItem('contacts')) || [],
    };
  },
  computed: {
    filteredContacts() {
      return this.contacts
        .filter(contact => {
          if (!contact || !contact.firstName || !contact.lastName) return false;
          const firstName = contact.firstName.toLowerCase();
          const lastName = contact.lastName.toLowerCase();
          return (
            firstName.includes(this.search.toLowerCase()) ||
            lastName.includes(this.search.toLowerCase())
          );
        })
        .sort((a, b) => a.lastName.localeCompare(b.lastName));
    },
  },
};
</script>

<style scoped>
.search-bar {
  width: 100%;
  padding: 10px;
  font-size: 1em;
  margin-bottom: 20px;
  border: 1px solid #ddd;
  border-radius: 4px;
}

.contact-list {
  list-style-type: circle;
  padding-left: 20px;
}

.contact-list li {
  margin: 10px 0;
  font-size: 1.2em;
}
</style>
