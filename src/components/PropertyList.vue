<script setup lang="ts">
import { defineProps } from 'vue'
import PropertyCard from './PropertyCard.vue'

defineProps<{
  properties: {
    id: number
    title: string
    description: string
    price: number
    location: string
    image: string
    bedrooms: number
    bathrooms: number
  }[]
}>()
</script>

<template>
  <div class="property-grid">
    <PropertyCard
      v-for="property in properties"
      :key="property.id"
      :property="property"
    />
  </div>
</template>

<style scoped>
.property-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 2rem;
  margin-top: 2rem;
}
</style>
