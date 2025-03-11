<script setup lang="ts">
import { ref } from 'vue'

const emit = defineEmits(['add-property'])

const newProperty = ref({
  title: '',
  description: '',
  price: 0,
  location: '',
  image: 'https://placehold.co/600x400',
  bedrooms: 1,
  bathrooms: 1
})

const submitForm = () => {
  emit('add-property', newProperty.value)
  newProperty.value = {
    title: '',
    description: '',
    price: 0,
    location: '',
    image: 'https://placehold.co/600x400',
    bedrooms: 1,
    bathrooms: 1
  }
}
</script>

<template>
  <div class="form-container">
    <h2>List Your Property</h2>
    <form @submit.prevent="submitForm">
      <div class="form-group">
        <label>Title:</label>
        <input v-model="newProperty.title" required />
      </div>
      <div class="form-group">
        <label>Description:</label>
        <textarea v-model="newProperty.description" required></textarea>
      </div>
      <div class="form-group">
        <label>Price ($):</label>
        <input v-model.number="newProperty.price" type="number" required />
      </div>
      <div class="form-group">
        <label>Location:</label>
        <input v-model="newProperty.location" required />
      </div>
      <div class="form-group">
        <label>Bedrooms:</label>
        <input v-model.number="newProperty.bedrooms" type="number" required />
      </div>
      <div class="form-group">
        <label>Bathrooms:</label>
        <input v-model.number="newProperty.bathrooms" type="number" required />
      </div>
      <button type="submit">Add Property</button>
    </form>
  </div>
</template>

<style scoped>
.form-container {
  background: #f5f5f5;
  padding: 2rem;
  border-radius: 8px;
  margin-bottom: 2rem;
}

.form-group {
  margin-bottom: 1rem;
}

label {
  display: block;
  margin-bottom: 0.5rem;
  color: #213547;
}

input,
textarea {
  width: 100%;
  padding: 0.5rem;
  border: 1px solid #ddd;
  border-radius: 4px;
}

button {
  background-color: #42b883;
  color: white;
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}

button:hover {
  background-color: #3aa876;
}
</style>
