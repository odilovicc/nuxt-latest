<template>
    <div class="modal">
      <div class="modal-content">
        <h2>Edit Cinema</h2>
        <label for="posterUrl">Poster URL:</label>
        <input type="text" v-model="editedCinema.posterUrl">
        <label for="name">Cinema Name:</label>
        <input type="text" v-model="editedCinema.name">
        <label for="author">Cinema Author:</label>
        <input type="text" v-model="editedCinema.author">
        <div class="buttons">
          <button @click="saveChanges">Save</button>
          <button @click="closeModal">Cancel</button>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const editedCinema = ref({});
  
  const saveChanges = () => {
    closeModal();
  };
  
  const closeModal = () => {
  };
  </script>
  