<script setup lang="ts">
import { ref } from 'vue'
import PropertyList from './components/PropertyList.vue'
import AddPropertyForm from './components/AddPropertyForm.vue'

interface Property {
  id: number
  title: string
  description: string
  price: number
  location: string
  image: string
  bedrooms: number
  bathrooms: number
}

const properties = ref<Property[]>([
  {
    id: 1,
    title: 'Modern Apartment in City Center',
    description: 'Spacious 2-bedroom apartment with great views',
    price: 2500,
    location: 'New York',
    image: 'https://placehold.co/600x400',
    bedrooms: 2,
    bathrooms: 2
  }
])

const addProperty = (property: Property) => {
  properties.value.push({
    ...property,
    id: properties.value.length + 1
  })
}
</script>

<template>
  <div class="container">
    <h1 class="title">Real Estate Marketplace</h1>
    <AddPropertyForm @add-property="addProperty" />
    <PropertyList :properties="properties" />
  </div>
</template>

<style>
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 2rem;
}

.title {
  text-align: center;
  margin-bottom: 2rem;
  color: #213547;
}
</style>
